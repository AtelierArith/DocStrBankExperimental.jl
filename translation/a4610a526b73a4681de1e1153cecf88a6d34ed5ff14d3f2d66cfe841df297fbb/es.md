```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Profile/docs/src/index.md"
```

# [Profiling](@id lib-profiling)

## CPU Profiling

Hay dos enfoques principales para el perfilado de CPU en código Julia:

## Via `@profile`

Donde el perfilado está habilitado para una llamada dada a través del macro `@profile`.

```julia-repl
julia> using Profile

julia> @profile foo()

julia> Profile.print()
Overhead ╎ [+additional indent] Count File:Line; Function
=========================================================
    ╎147  @Base/client.jl:506; _start()
        ╎ 147  @Base/client.jl:318; exec_options(opts::Base.JLOptions)
...
```

## Triggered During Execution

Las tareas que ya están en ejecución también se pueden perfilar durante un período de tiempo fijo en cualquier momento activado por el usuario.

Para activar el perfilado:

  * MacOS y FreeBSD (plataformas basadas en BSD): Usa `ctrl-t` o envía una señal `SIGINFO` al proceso de julia, es decir, `% kill -INFO $julia_pid`
  * Linux: Envía una señal `SIGUSR1` al proceso de julia es decir, `% kill -USR1 $julia_pid`
  * Windows: No compatible actualmente.

Primero, se muestra un único rastreo de pila en el instante en que se lanzó la señal, luego se recopila un perfil de 1 segundo, seguido del informe del perfil en el siguiente punto de ceder, que puede ser al completar la tarea para código sin puntos de ceder, por ejemplo, bucles ajustados.

Opcionalmente, establece la variable de entorno [`JULIA_PROFILE_PEEK_HEAP_SNAPSHOT`](@ref JULIA_PROFILE_PEEK_HEAP_SNAPSHOT) en `1` para también recopilar automáticamente un [heap snapshot](@ref Heap-Snapshots).

```julia-repl
julia> foo()
##== the user sends a trigger while foo is running ==##
load: 2.53  cmd: julia 88903 running 6.16u 0.97s

======================================================================================
Information request received. A stacktrace will print followed by a 1.0 second profile
======================================================================================

signal (29): Information request: 29
__psynch_cvwait at /usr/lib/system/libsystem_kernel.dylib (unknown line)
_pthread_cond_wait at /usr/lib/system/libsystem_pthread.dylib (unknown line)
...

======================================================================
Profile collected. A report will print if the Profile module is loaded
======================================================================

Overhead ╎ [+additional indent] Count File:Line; Function
=========================================================
Thread 1 Task 0x000000011687c010 Total snapshots: 572. Utilization: 100%
   ╎147 @Base/client.jl:506; _start()
       ╎ 147 @Base/client.jl:318; exec_options(opts::Base.JLOptions)
...

Thread 2 Task 0x0000000116960010 Total snapshots: 572. Utilization: 0%
   ╎572 @Base/task.jl:587; task_done_hook(t::Task)
      ╎ 572 @Base/task.jl:879; wait()
...
```

### Customization

La duración del perfilado se puede ajustar a través de [`Profile.set_peek_duration`](@ref)

El informe de perfil se desglosa por hilo y tarea. Pasa una función sin argumentos a `Profile.peek_report[]` para anular esto. es decir, `Profile.peek_report[] = () -> Profile.print()` para eliminar cualquier agrupación. Esto también podría ser anulado por un consumidor de datos de perfil externo.

## Reference

```@docs
Profile.@profile
```

Los métodos en `Profile` no están exportados y deben ser llamados, por ejemplo, como `Profile.print()`.

```@docs
Profile.clear
Profile.print
Profile.init
Profile.fetch
Profile.retrieve
Profile.callers
Profile.clear_malloc_data
Profile.get_peek_duration
Profile.set_peek_duration
```

## Memory profiling

```@docs
Profile.Allocs.@profile
```

Los métodos en `Profile.Allocs` no están exportados y deben ser llamados, por ejemplo, como `Profile.Allocs.fetch()`.

```@docs
Profile.Allocs.clear
Profile.Allocs.print
Profile.Allocs.fetch
Profile.Allocs.start
Profile.Allocs.stop
```

## Heap Snapshots

```@docs
Profile.take_heap_snapshot
```

Los métodos en `Profile` no están exportados y deben ser llamados, por ejemplo, como `Profile.take_heap_snapshot()`.

```julia-repl
julia> using Profile

julia> Profile.take_heap_snapshot("snapshot.heapsnapshot")
```

Rastrea y registra objetos de Julia en el heap. Esto solo registra objetos conocidos por el recolector de basura de Julia. La memoria asignada por bibliotecas externas no gestionadas por el recolector de basura no aparecerá en la instantánea.

Para evitar OOM al grabar la instantánea, añadimos una opción de transmisión para enviar la instantánea del montón a cuatro archivos,

```julia-repl
julia> using Profile

julia> Profile.take_heap_snapshot("snapshot"; streaming=true)
```

donde "snapshot" es la ruta del archivo como prefijo para los archivos generados.

Una vez que se generan los archivos de instantánea, se pueden ensamblar sin conexión con el siguiente comando:

```julia-repl
julia> using Profile

julia> Profile.HeapSnapshot.assemble_snapshot("snapshot", "snapshot.heapsnapshot")
```

El archivo de instantánea de heap resultante se puede cargar en chrome devtools para ser visualizado. Para más información, consulta el [chrome devtools docs](https://developer.chrome.com/docs/devtools/memory-problems/heap-snapshots/#view_snapshots). Una alternativa para analizar instantáneas de heap de Chromium es con la extensión de VS Code `ms-vscode.vscode-js-profile-flame`.

Las instantáneas de heap de Firefox son de un formato diferente, y actualmente Firefox *no* puede ser utilizado para ver las instantáneas de heap generadas por Julia.
