# Instrumenting Julia with DTrace, and bpftrace

DTrace y bpftrace son herramientas que permiten la instrumentación ligera de procesos. Puedes activar y desactivar la instrumentación mientras el proceso está en ejecución, y con la instrumentación desactivada, la sobrecarga es mínima.

!!! compat "Julia 1.8"
    El soporte para probes se agregó en Julia 1.8


!!! note
    Esta documentación ha sido escrita desde una perspectiva de Linux, la mayor parte de esto debería ser aplicable en Mac OS/Darwin y FreeBSD.


## Enabling support

En Linux, instala el paquete `systemtap` que tiene una versión de `dtrace` y crea un archivo `Make.user` que contenga

```
WITH_DTRACE=1
```

para habilitar las sondas de USDT.

### Verifying

```
> readelf -n usr/lib/libjulia-internal.so.1

Displaying notes found in: .note.gnu.build-id
  Owner                Data size  Description
  GNU                  0x00000014 NT_GNU_BUILD_ID (unique build ID bitstring)
    Build ID: 57161002f35548772a87418d2385c284ceb3ead8

Displaying notes found in: .note.stapsdt
  Owner                Data size  Description
  stapsdt              0x00000029 NT_STAPSDT (SystemTap probe descriptors)
    Provider: julia
    Name: gc__begin
    Location: 0x000000000013213e, Base: 0x00000000002bb4da, Semaphore: 0x0000000000346cac
    Arguments:
  stapsdt              0x00000032 NT_STAPSDT (SystemTap probe descriptors)
    Provider: julia
    Name: gc__stop_the_world
    Location: 0x0000000000132144, Base: 0x00000000002bb4da, Semaphore: 0x0000000000346cae
    Arguments:
  stapsdt              0x00000027 NT_STAPSDT (SystemTap probe descriptors)
    Provider: julia
    Name: gc__end
    Location: 0x000000000013214a, Base: 0x00000000002bb4da, Semaphore: 0x0000000000346cb0
    Arguments:
  stapsdt              0x0000002d NT_STAPSDT (SystemTap probe descriptors)
    Provider: julia
    Name: gc__finalizer
    Location: 0x0000000000132150, Base: 0x00000000002bb4da, Semaphore: 0x0000000000346cb2
    Arguments:
```

## Adding probes in libjulia

Las sondas se declaran en formato dtraces en el archivo `src/uprobes.d`. El archivo de encabezado generado se incluye en `src/julia_internal.h` y si agregas sondas, debes proporcionar una implementación noop allí.

El encabezado contendrá un semáforo `*_ENABLED` y la llamada real a la sonda. Si los argumentos de la sonda son costosos de calcular, primero debes verificar si la sonda está habilitada y luego calcular los argumentos y llamar a la sonda.

```c
  if (JL_PROBE_{PROBE}_ENABLED())
    auto expensive_arg = ...;
    JL_PROBE_{PROBE}(expensive_arg);
```

Si su sonda no tiene argumentos, se prefiere no incluir la verificación del semáforo. Con las sondas USDT habilitadas, el costo de un semáforo es una carga de memoria, independientemente de si la sonda está habilitada o no.

```c
#define JL_PROBE_GC_BEGIN_ENABLED() __builtin_expect (julia_gc__begin_semaphore, 0)
__extension__ extern unsigned short julia_gc__begin_semaphore __attribute__ ((unused)) __attribute__ ((section (".probes")));
```

Mientras que la sonda en sí es un trineo noop que será conectado a una trampa para el manejador de la sonda.

## Available probes

### GC probes

1. `julia:gc__begin`: El GC comienza a ejecutarse en un hilo y activa la detención del mundo.
2. `julia:gc__stop_the_world`: Todos los hilos han alcanzado un punto seguro y se ejecuta el GC.
3. `julia:gc__mark__begin`: Comenzando la fase de marcado
4. `julia:gc__mark_end(scanned_bytes, perm_scanned)`: La fase de marcado ha terminado
5. `julia:gc__sweep_begin(full)`: Comenzando barrido
6. `julia:gc__sweep_end`: Fase de barrido finalizada
7. `julia:gc__end`: GC ha terminado, otros hilos continúan trabajando
8. `julia:gc__finalizer`: El hilo inicial de GC ha terminado de ejecutar los finalizadores

### Task runtime probes

1. `julia:rt__run__task(task)`: Cambiando a la tarea `task` en el hilo actual.
2. `julia:rt__pause__task(task)`: Cambiando de la tarea `task` en el hilo actual.
3. `julia:rt__new__task(parent, child)`: La tarea `parent` creó la tarea `child` en el hilo actual.
4. `julia:rt__start__task(task)`: Tarea `task` iniciada por primera vez con una nueva pila.
5. `julia:rt__finish__task(tarea)`: La tarea `tarea` ha finalizado y ya no se ejecutará.
6. `julia:rt__start__process__events(task)`: La tarea `task` comenzó a procesar eventos de libuv.
7. `julia:rt__finish__process__events(tarea)`: La tarea `tarea` terminó de procesar eventos de libuv.

### Task queue probes

1. `julia:rt__taskq__insert(ptls, task)`: El hilo `ptls` intentó insertar `task` en un PARTR multiq.
2. `julia:rt__taskq__get(ptls, task)`: El hilo `ptls` sacó `task` de una cola multiq PARTR.

### Thread sleep/wake probes

1. `julia:rt__sleep__check__wake(ptls, old_state)`: Hilo (PTLS `ptls`) despertando, previamente en el estado `old_state`.
2. `julia:rt__sleep__check__wakeup(ptls)`: El hilo (PTLS `ptls`) se despertó a sí mismo.
3. `julia:rt__sleep__check__sleep(ptls)`: El hilo (PTLS `ptls`) está intentando dormir.
4. `julia:rt__sleep__check__taskq__wake(ptls)`: El hilo (PTLS `ptls`) no puede dormir debido a tareas en PARTR multiq.
5. `julia:rt__sleep__check__task__wake(ptls)`: El hilo (PTLS `ptls`) no puede dormir debido a tareas en la cola de trabajo de Base.
6. `julia:rt__sleep__check__uv__wake(ptls)`: El hilo (PTLS `ptls`) no puede dormir debido a la activación de libuv.

## Probe usage examples

### GC stop-the-world latency

Un ejemplo de script `bpftrace` se encuentra en `contrib/gc_stop_the_world_latency.bt` y crea un histograma de la latencia para que todos los hilos alcancen un punto seguro.

Ejecutando este código de Julia, con `julia -t 2`

```
using Base.Threads

fib(x) = x <= 1 ? 1 : fib(x-1) + fib(x-2)

beaver = @spawn begin
    while true
        fib(30)
        # A manual safepoint is necessary since otherwise this loop
        # may never yield to GC.
        GC.safepoint()
    end
end

allocator = @spawn begin
    while true
        zeros(1024)
    end
end

wait(allocator)
```

y en una segunda terminal

```
> sudo contrib/bpftrace/gc_stop_the_world_latency.bt
Attaching 4 probes...
Tracing Julia GC Stop-The-World Latency... Hit Ctrl-C to end.
^C


@usecs[1743412]:
[4, 8)               971 |@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@|
[8, 16)              837 |@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@        |
[16, 32)             129 |@@@@@@                                              |
[32, 64)              10 |                                                    |
[64, 128)              1 |                                                    |
```

Podemos ver la distribución de latencia de la fase de detención del mundo en el proceso de Julia ejecutado.

### Task spawn monitor

A veces es útil saber cuándo una tarea está generando otras tareas. Esto es muy fácil de ver con `rt__new__task`. El primer argumento de la sonda, `parent`, es la tarea existente que está creando una nueva tarea. Esto significa que si conoces la dirección de la tarea que deseas monitorear, puedes ver fácilmente las tareas que esa tarea específica generó. Veamos cómo hacer esto; primero, comencemos una sesión de Julia y obtengamos el PID y la dirección de la tarea del REPL:

```
> julia
               _
   _       _ _(_)_     |  Documentation: https://docs.julialang.org
  (_)     | (_) (_)    |
   _ _   _| |_  __ _   |  Type "?" for help, "]?" for Pkg help.
  | | | | | | |/ _` |  |
  | | |_| | | | (_| |  |  Version 1.6.2 (2021-07-14)
 _/ |\__'_|_|_|\__'_|  |  Official https://julialang.org/ release
|__/                   |

1> getpid()
997825

2> current_task()
Task (runnable) @0x00007f524d088010
```

Ahora podemos iniciar `bpftrace` y hacer que monitoree `rt__new__task` solo para este padre:

`sudo bpftrace -p 997825 -e 'usdt:usr/lib/libjulia-internal.so:julia:rt__new__task /arg0==0x00007f524d088010/{ printf("Tarea: %x\n", arg0); }'`

(Tenga en cuenta que en lo anterior, `arg0` es el primer argumento, `parent`).

Y si generamos una sola tarea:

`@async 1+1`

vemos que esta tarea está siendo creada:

`Tarea: 4d088010`

Sin embargo, si generamos un montón de tareas a partir de esa tarea recién generada:

```julia
@async for i in 1:10
   @async 1+1
end
```

todavía solo vemos una tarea de `bpftrace`:

`Tarea: 4d088010`

y sigue siendo la misma tarea que estábamos monitoreando. Por supuesto, podemos eliminar este filtro para ver *todas* las tareas recién creadas con la misma facilidad:

`sudo bpftrace -p 997825 -e 'usdt:usr/lib/libjulia-internal.so:julia:rt__new__task { printf("Tarea: %x\n", arg0); }'`

```
Task: 4d088010
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
```

Podemos ver nuestra tarea raíz y la tarea recién creada como la madre de las diez tareas aún más nuevas.

### Thundering herd detection

Los tiempos de ejecución de tareas a menudo pueden sufrir del problema de "manada atronadora": cuando se agrega trabajo a un tiempo de ejecución de tareas tranquilo, todos los hilos pueden ser despertados de su letargo, incluso si no hay suficiente trabajo para que cada hilo lo procese. Esto puede causar latencia adicional y ciclos de CPU mientras todos los hilos se despiertan (y simultáneamente vuelven a dormir, sin encontrar trabajo que ejecutar).

Podemos ver este problema ilustrado con `bpftrace` bastante fácilmente. Primero, en una terminal iniciamos Julia con múltiples hilos (6 en este ejemplo), y obtenemos el PID de ese proceso:

```
> julia -t 6
               _
   _       _ _(_)_     |  Documentation: https://docs.julialang.org
  (_)     | (_) (_)    |
   _ _   _| |_  __ _   |  Type "?" for help, "]?" for Pkg help.
  | | | | | | |/ _` |  |
  | | |_| | | | (_| |  |  Version 1.6.2 (2021-07-14)
 _/ |\__'_|_|_|\__'_|  |  Official https://julialang.org/ release
|__/                   |

1> getpid()
997825
```

Y en otra terminal comenzamos a monitorear nuestro proceso con `bpftrace`, específicamente sondeando el gancho `rt__sleep__check__wake`:

`sudo bpftrace -p 997825 -e 'usdt:usr/lib/libjulia-internal.so:julia:rt__sleep__check__wake { printf("¡Hilo despertado! %x\n", arg0); }'`

Ahora, creamos y ejecutamos una única tarea en Julia:

`Threads.@spawn 1+1`

Y en `bpftrace` vemos impreso algo como:

```
Thread wake up! 3f926100
Thread wake up! 3ebd5140
Thread wake up! 3f876130
Thread wake up! 3e2711a0
Thread wake up! 3e312190
```

Aunque solo generamos una única tarea (que solo un hilo podía procesar a la vez), ¡despertamos a todos nuestros otros hilos! En el futuro, un runtime de tareas más inteligente podría despertar solo un hilo (o ninguno; ¡el hilo que la generó podría ejecutar esta tarea!), y deberíamos ver que este comportamiento desaparezca.

### Task Monitor with BPFnative.jl

BPFnative.jl es capaz de adjuntarse a los puntos de sonda USDT al igual que `bpftrace`. Hay una demostración disponible para monitorear el tiempo de ejecución de tareas, GC y transiciones de sueño/despertar de hilos [here](https://github.com/jpsamaroo/BPFnative.jl/blob/master/examples/task-runtime.jl).

## Notes on using `bpftrace`

Un ejemplo de sonda en el formato bpftrace se ve así:

```
usdt:usr/lib/libjulia-internal.so:julia:gc__begin
{
  @start[pid] = nsecs;
}
```

La declaración de la sonda toma el tipo `usdt`, luego ya sea la ruta a la biblioteca o el PID, el nombre del proveedor `julia` y el nombre de la sonda `gc__begin`. Tenga en cuenta que estoy utilizando una ruta relativa a `libjulia-internal.so`, pero esto podría necesitar ser una ruta absoluta en un sistema de producción.

## Useful references:

  * [Julia Evans blog on Linux tracing systems](https://jvns.ca/blog/2017/07/05/linux-tracing-systems)
  * [LWN article on USDT and BPF](https://lwn.net/Articles/753601/)
  * [GDB support for probes](https://sourceware.org/gdb/onlinedocs/gdb/Static-Probe-Points.html)
  * [Brendan Gregg – Linux Performance](https://www.brendangregg.com/linuxperf.html)
