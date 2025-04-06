# [Multi-Threading](@id man-multithreading)

Visita este [blog post](https://julialang.org/blog/2019/07/multithreading/) para una presentación de las características de multi-hilo de Julia.

## Starting Julia with multiple threads

Por defecto, Julia se inicia con un solo hilo de ejecución. Esto se puede verificar utilizando el comando [`Threads.nthreads()`](@ref):

```jldoctest
julia> Threads.nthreads()
1
```

El número de hilos de ejecución se controla ya sea utilizando el argumento de línea de comandos `-t`/`--threads` o utilizando la variable de entorno [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS). Cuando ambos se especifican, entonces `-t`/`--threads` tiene prioridad.

El número de hilos se puede especificar como un entero (`--threads=4`) o como `auto` (`--threads=auto`), donde `auto` intenta inferir un número útil de hilos a utilizar (ver [Command-line Options](@ref command-line-interface) para más detalles).

!!! compat "Julia 1.5"
    El argumento de línea de comandos `-t`/`--threads` requiere al menos Julia 1.5. En versiones anteriores, debes usar la variable de entorno en su lugar.


!!! compat "Julia 1.7"
    Usar `auto` como valor de la variable de entorno [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS) requiere al menos Julia 1.7. En versiones anteriores, este valor es ignorado.


Comencemos Julia con 4 hilos:

```bash
$ julia --threads 4
```

Verifiquemos que hay 4 hilos a nuestra disposición.

```julia-repl
julia> Threads.nthreads()
4
```

Pero actualmente estamos en el hilo principal. Para verificar, usamos la función [`Threads.threadid`](@ref)

```jldoctest
julia> Threads.threadid()
1
```

!!! note
    Si prefieres usar la variable de entorno, puedes configurarla de la siguiente manera en Bash (Linux/macOS):

    ```bash
    export JULIA_NUM_THREADS=4
    ```

    C shell en Linux/macOS, CMD en Windows:

    ```bash
    set JULIA_NUM_THREADS=4
    ```

    Powershell en Windows:

    ```powershell
    $env:JULIA_NUM_THREADS=4
    ```

    Tenga en cuenta que esto debe hacerse *antes* de iniciar Julia.


!!! note
    El número de hilos especificado con `-t`/`--threads` se propaga a los procesos de trabajo que se generan utilizando las opciones de línea de comandos `-p`/`--procs` o `--machine-file`. Por ejemplo, `julia -p2 -t2` genera 1 proceso principal con 2 procesos de trabajo, y los tres procesos tienen 2 hilos habilitados. Para un control más detallado sobre los hilos de trabajo, utiliza [`addprocs`](@ref) y pasa `-t`/`--threads` como `exeflags`.


### Multiple GC Threads

El recolector de basura (GC) puede usar múltiples hilos. La cantidad utilizada es la mitad del número de hilos de trabajo de cómputo o se configura mediante el argumento de línea de comandos `--gcthreads` o utilizando la variable de entorno [`JULIA_NUM_GC_THREADS`](@ref JULIA_NUM_GC_THREADS).

!!! compat "Julia 1.10"
    El argumento de línea de comando `--gcthreads` requiere al menos Julia 1.10.


## [Threadpools](@id man-threadpools)

Cuando los hilos de un programa están ocupados con muchas tareas por ejecutar, las tareas pueden experimentar retrasos que pueden afectar negativamente la capacidad de respuesta y la interactividad del programa. Para abordar esto, puedes especificar que una tarea es interactiva cuando [`Threads.@spawn`](@ref) lo:

```julia
using Base.Threads
@spawn :interactive f()
```

Las tareas interactivas deben evitar realizar operaciones de alta latencia, y si son tareas de larga duración, deben ceder con frecuencia.

Julia se puede iniciar con uno o más hilos reservados para ejecutar tareas interactivas:

```bash
$ julia --threads 3,1
```

La variable de entorno [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS) también se puede usar de manera similar:

```bash
export JULIA_NUM_THREADS=3,1
```

Esto inicia Julia con 3 hilos en el grupo de hilos `:default` y 1 hilo en el grupo de hilos `:interactive`:

```julia-repl
julia> using Base.Threads

julia> nthreadpools()
2

julia> threadpool() # the main thread is in the interactive thread pool
:interactive

julia> nthreads(:default)
3

julia> nthreads(:interactive)
1

julia> nthreads()
3
```

!!! note
    La versión sin argumentos de `nthreads` devuelve el número de hilos en el grupo predeterminado.


!!! note
    Dependiendo de si Julia se ha iniciado con hilos interactivos, el hilo principal está en el grupo de hilos predeterminado o en el grupo de hilos interactivos.


Cualquiera de los dos números puede ser reemplazado por la palabra `auto`, lo que hace que Julia elija un valor predeterminado razonable.

## The `@threads` Macro

Vamos a trabajar un ejemplo simple usando nuestros hilos nativos. Creamos un array de ceros:

```jldoctest
julia> a = zeros(10)
10-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
```

Operemos en este arreglo simultáneamente utilizando 4 hilos. Haremos que cada hilo escriba su ID de hilo en cada ubicación.

Julia admite bucles paralelos utilizando el macro [`Threads.@threads`](@ref). Este macro se coloca delante de un bucle `for` para indicar a Julia que el bucle es una región de múltiples hilos:

```julia-repl
julia> Threads.@threads for i = 1:10
           a[i] = Threads.threadid()
       end
```

El espacio de iteración se divide entre los hilos, después de lo cual cada hilo escribe su ID de hilo en sus ubicaciones asignadas:

```julia-repl
julia> a
10-element Vector{Float64}:
 1.0
 1.0
 1.0
 2.0
 2.0
 2.0
 3.0
 3.0
 4.0
 4.0
```

Tenga en cuenta que [`Threads.@threads`](@ref) no tiene un parámetro de reducción opcional como [`@distributed`](@ref).

### Using `@threads` without data-races

El concepto de una carrera de datos se elabora en ["Communication and data races between threads"](@ref man-communication-and-data-races). Por ahora, solo se debe saber que una carrera de datos puede resultar en resultados incorrectos y errores peligrosos.

Supongamos que queremos hacer que la función `sum_single` a continuación sea multihilo.

```julia-repl
julia> function sum_single(a)
           s = 0
           for i in a
               s += i
           end
           s
       end
sum_single (generic function with 1 method)

julia> sum_single(1:1_000_000)
500000500000
```

Simplemente agregar `@threads` expone una carrera de datos con múltiples hilos leyendo y escribiendo `s` al mismo tiempo.

```julia-repl
julia> function sum_multi_bad(a)
           s = 0
           Threads.@threads for i in a
               s += i
           end
           s
       end
sum_multi_bad (generic function with 1 method)

julia> sum_multi_bad(1:1_000_000)
70140554652
```

Tenga en cuenta que el resultado no es `500000500000` como debería ser, y lo más probable es que cambie en cada evaluación.

Para solucionar esto, se pueden utilizar búferes específicos para la tarea para segmentar la suma en partes que estén libres de condiciones de carrera. Aquí `sum_single` se reutiliza, con su propio búfer interno `s`. El vector de entrada `a` se divide en `nthreads()` partes para el trabajo en paralelo. Luego usamos `Threads.@spawn` para crear tareas que sumen individualmente cada parte. Finalmente, sumamos los resultados de cada tarea utilizando `sum_single` nuevamente:

```julia-repl
julia> function sum_multi_good(a)
           chunks = Iterators.partition(a, length(a) ÷ Threads.nthreads())
           tasks = map(chunks) do chunk
               Threads.@spawn sum_single(chunk)
           end
           chunk_sums = fetch.(tasks)
           return sum_single(chunk_sums)
       end
sum_multi_good (generic function with 1 method)

julia> sum_multi_good(1:1_000_000)
500000500000
```

!!! note
    Los búferes no deben ser gestionados en función de `threadid()`, es decir, `buffers = zeros(Threads.nthreads())`, porque las tareas concurrentes pueden ceder, lo que significa que múltiples tareas concurrentes pueden usar el mismo búfer en un hilo dado, introduciendo el riesgo de condiciones de carrera. Además, cuando hay más de un hilo disponible, las tareas pueden cambiar de hilo en los puntos de ceder, lo que se conoce como [task migration](@ref man-task-migration).


Otra opción es el uso de operaciones atómicas en variables compartidas entre tareas/hilos, lo que puede ser más eficiente dependiendo de las características de las operaciones.

## [Communication and data-races between threads](@id man-communication-and-data-races)

Aunque los hilos de Julia pueden comunicarse a través de memoria compartida, es notoriamente difícil escribir código multihilo correcto y libre de condiciones de carrera. Los [`Channel`](@ref) de Julia son seguros para hilos y pueden usarse para comunicarse de manera segura. También hay secciones a continuación que explican cómo usar [locks](@ref man-using-locks) y [atomics](@ref man-atomic-operations) para evitar condiciones de carrera.

### Data-race freedom

Eres completamente responsable de garantizar que tu programa esté libre de condiciones de carrera, y nada de lo que se promete aquí se puede asumir si no cumples con ese requisito. Los resultados observados pueden ser altamente contraintuitivos.

Si se introducen condiciones de carrera, Julia no es segura en cuanto a la memoria. **Ten mucho cuidado al leer *cualquier* dato si otro hilo podría escribir en él, ya que podría resultar en fallos de segmentación o algo peor**. A continuación se presentan un par de formas inseguras de acceder a variables globales desde diferentes hilos:

```julia
Thread 1:
global b = false
global a = rand()
global b = true

Thread 2:
while !b; end
bad_read1(a) # it is NOT safe to access `a` here!

Thread 3:
while !@isdefined(a); end
bad_read2(a) # it is NOT safe to access `a` here
```

### [Using locks to avoid data-races](@id man-using-locks)

Una herramienta importante para evitar condiciones de carrera y, por lo tanto, escribir código seguro para hilos, es el concepto de un "bloqueo". Un bloqueo puede ser bloqueado y desbloqueado. Si un hilo ha bloqueado un bloqueo y no lo ha desbloqueado, se dice que "sostiene" el bloqueo. Si hay solo un bloqueo y escribimos código que requiere sostener el bloqueo para acceder a algunos datos, podemos asegurarnos de que múltiples hilos nunca accedan a los mismos datos simultáneamente. Tenga en cuenta que la conexión entre un bloqueo y una variable es realizada por el programador, y no por el programa.

Por ejemplo, podemos crear un bloqueo `my_lock` y bloquearlo mientras mutamos una variable `my_variable`. Esto se hace de la manera más simple con el macro `@lock`:

```julia-repl
julia> my_lock = ReentrantLock();

julia> my_variable = [1, 2, 3];

julia> @lock my_lock my_variable[1] = 100
100
```

Al utilizar un patrón similar con el mismo bloqueo y variable, pero en otro hilo, las operaciones están libres de condiciones de carrera.

Podríamos haber realizado la operación anterior con la versión funcional de `lock`, de las siguientes dos maneras:

```julia-repl
julia> lock(my_lock) do
           my_variable[1] = 100
       end
100

julia> begin
           lock(my_lock)
           try
               my_variable[1] = 100
           finally
               unlock(my_lock)
           end
       end
100
```

Las tres opciones son equivalentes. Nota cómo la versión final requiere un bloque `try` explícito para asegurar que el bloqueo siempre se desbloquee, mientras que las dos primeras versiones lo hacen internamente. Siempre se debe usar el patrón de bloqueo anterior al cambiar datos (como asignar a una variable global o de cierre) accesibles por otros hilos. No hacerlo podría tener consecuencias imprevistas y graves.

### [Atomic Operations](@id man-atomic-operations)

Julia admite el acceso y la modificación de valores *atómicamente*, es decir, de una manera segura para hilos para evitar [race conditions](https://en.wikipedia.org/wiki/Race_condition). Un valor (que debe ser de un tipo primitivo) puede ser envuelto como [`Threads.Atomic`](@ref) para indicar que debe ser accedido de esta manera. Aquí podemos ver un ejemplo:

```julia-repl
julia> i = Threads.Atomic{Int}(0);

julia> ids = zeros(4);

julia> old_is = zeros(4);

julia> Threads.@threads for id in 1:4
           old_is[id] = Threads.atomic_add!(i, id)
           ids[id] = id
       end

julia> old_is
4-element Vector{Float64}:
 0.0
 1.0
 7.0
 3.0

julia> i[]
 10

julia> ids
4-element Vector{Float64}:
 1.0
 2.0
 3.0
 4.0
```

Si hubiéramos intentado hacer la suma sin la etiqueta atómica, podríamos haber obtenido la respuesta incorrecta debido a una condición de carrera. Un ejemplo de lo que sucedería si no evitáramos la carrera:

```julia-repl
julia> using Base.Threads

julia> Threads.nthreads()
4

julia> acc = Ref(0)
Base.RefValue{Int64}(0)

julia> @threads for i in 1:1000
          acc[] += 1
       end

julia> acc[]
926

julia> acc = Atomic{Int64}(0)
Atomic{Int64}(0)

julia> @threads for i in 1:1000
          atomic_add!(acc, 1)
       end

julia> acc[]
1000
```

#### [Per-field atomics](@id man-atomics)

También podemos usar atómicos a un nivel más granular utilizando los macros [`@atomic`](@ref Base.@atomic), [`@atomicswap`](@ref Base.@atomicswap), [`@atomicreplace`](@ref Base.@atomicreplace) y [`@atomiconce`](@ref Base.@atomiconce).

Los detalles específicos del modelo de memoria y otros detalles del diseño están escritos en el [Julia Atomics Manifesto](https://gist.github.com/vtjnash/11b0031f2e2a66c9c24d33e810b34ec0), que se publicará formalmente más adelante.

Cualquier campo en una declaración de struct puede ser decorado con `@atomic`, y luego cualquier escritura debe estar marcada también con `@atomic` y debe usar uno de los ordenamientos atómicos definidos (`:monotonic`, `:acquire`, `:release`, `:acquire_release` o `:sequentially_consistent`). Cualquier lectura de un campo atómico también puede ser anotada con una restricción de ordenamiento atómico, o se realizará con un ordenamiento monótono (relajado) si no se especifica.

!!! compat "Julia 1.7"
    Las atomics por campo requieren al menos Julia 1.7.


## Side effects and mutable function arguments

Cuando se utiliza multi-threading, debemos tener cuidado al usar funciones que no son [pure](https://en.wikipedia.org/wiki/Pure_function) ya que podríamos obtener una respuesta incorrecta. Por ejemplo, las funciones que tienen un [name ending with `!`](@ref bang-convention) por convención modifican sus argumentos y, por lo tanto, no son puras.

## @threadcall

Las bibliotecas externas, como las que se llaman a través de [`ccall`](@ref), representan un problema para el mecanismo de E/S basado en tareas de Julia. Si una biblioteca C realiza una operación bloqueante, eso impide que el programador de Julia ejecute otras tareas hasta que la llamada regrese. (Las excepciones son las llamadas a código C personalizado que llaman de vuelta a Julia, que pueden ceder, o el código C que llama a `jl_yield()`, el equivalente en C de [`yield`](@ref).)

El macro [`@threadcall`](@ref) proporciona una forma de evitar la detención de la ejecución en tal escenario. Programa una función C para su ejecución en un hilo separado. Se utiliza un grupo de hilos con un tamaño predeterminado de 4 para esto. El tamaño del grupo de hilos se controla a través de la variable de entorno `UV_THREADPOOL_SIZE`. Mientras espera un hilo libre, y durante la ejecución de la función una vez que un hilo está disponible, la tarea solicitante (en el bucle de eventos principal de Julia) cede a otras tareas. Tenga en cuenta que `@threadcall` no devuelve hasta que la ejecución se completa. Desde el punto de vista del usuario, por lo tanto, es una llamada bloqueante como otras API de Julia.

Es muy importante que la función llamada no vuelva a llamar a Julia, ya que causará un fallo de segmentación.

`@threadcall` puede ser eliminado/cambiado en futuras versiones de Julia.

## Caveats

En este momento, la mayoría de las operaciones en el tiempo de ejecución de Julia y las bibliotecas estándar se pueden utilizar de manera segura en hilos, si el código del usuario es libre de condiciones de carrera. Sin embargo, en algunas áreas, se está trabajando en estabilizar el soporte para hilos. La programación multihilo tiene muchas dificultades inherentes, y si un programa que utiliza hilos exhibe un comportamiento inusual o indeseable (por ejemplo, bloqueos o resultados misteriosos), las interacciones entre hilos deberían ser sospechadas primero.

Hay algunas limitaciones y advertencias específicas que debes tener en cuenta al usar hilos en Julia:

  * Los tipos de colecciones base requieren bloqueo manual si son utilizados simultáneamente por múltiples hilos donde al menos un hilo modifica la colección (ejemplos comunes incluyen `push!` en arreglos, o insertar elementos en un `Dict`).
  * El horario utilizado por [`@spawn`](@ref Threads.@spawn) es no determinista y no debe ser confiado.
  * Las tareas limitadas por la CPU y que no asignan memoria pueden impedir que la recolección de basura se ejecute en otros hilos que están asignando memoria. En estos casos, puede ser necesario insertar una llamada manual a `GC.safepoint()` para permitir que la recolección de basura se ejecute. Esta limitación se eliminará en el futuro.
  * Evite ejecutar operaciones de nivel superior, por ejemplo, `include`, o `eval` de definiciones de tipo, método y módulo en paralelo.
  * Be aware that finalizers registered by a library may break if threads are enabled. This may require some transitional work across the ecosystem before threading can be widely adopted with confidence. See the section on [the safe use of finalizers](@ref man-finalizers) for further details.

## [Task Migration](@id man-task-migration)

Después de que una tarea comienza a ejecutarse en un cierto hilo, puede moverse a un hilo diferente si la tarea cede.

Tales tareas pueden haber comenzado con [`@spawn`](@ref Threads.@spawn) o [`@threads`](@ref Threads.@threads), aunque la opción de programación `:static` para `@threads` congela el threadid.

Esto significa que en la mayoría de los casos [`threadid()`](@ref Threads.threadid) no debe ser tratado como constante dentro de una tarea, y por lo tanto no debe ser utilizado para indexar en un vector de buffers u objetos con estado.

!!! compat "Julia 1.7"
    La migración de tareas se introdujo en Julia 1.7. Antes de esto, las tareas siempre permanecían en el mismo hilo en el que se iniciaron.


## [Safe use of Finalizers](@id man-finalizers)

Debido a que los finalizadores pueden interrumpir cualquier código, deben tener mucho cuidado en cómo interactúan con cualquier estado global. Desafortunadamente, la razón principal por la que se utilizan los finalizadores es para actualizar el estado global (una función pura es generalmente bastante inútil como finalizador). Esto nos lleva a un pequeño dilema. Hay algunos enfoques para abordar este problema:

1. Cuando se ejecuta en un solo hilo, el código podría llamar a la función C interna `jl_gc_enable_finalizers` para evitar que se programen finalizadores dentro de una región crítica. Internamente, esto se utiliza dentro de algunas funciones (como nuestros bloqueos en C) para prevenir la recursión al realizar ciertas operaciones (carga incremental de paquetes, generación de código, etc.). La combinación de un bloqueo y esta bandera se puede utilizar para hacer que los finalizadores sean seguros.
2. Una segunda estrategia, empleada por Base en un par de lugares, es retrasar explícitamente un finalizador hasta que pueda adquirir su bloqueo de manera no recursiva. El siguiente ejemplo demuestra cómo se podría aplicar esta estrategia a `Distributed.finalize_ref`:

    ```julia
    function finalize_ref(r::AbstractRemoteRef)
        if r.where > 0 # Check if the finalizer is already run
            if islocked(client_refs) || !trylock(client_refs)
                # delay finalizer for later if we aren't free to acquire the lock
                finalizer(finalize_ref, r)
                return nothing
            end
            try # `lock` should always be followed by `try`
                if r.where > 0 # Must check again here
                    # Do actual cleanup here
                    r.where = 0
                end
            finally
                unlock(client_refs)
            end
        end
        nothing
    end
    ```
3. Una tercera estrategia relacionada es utilizar una cola sin rendimiento. Actualmente no tenemos una cola sin bloqueo implementada en Base, pero `Base.IntrusiveLinkedListSynchronized{T}` es adecuada. Esta puede ser frecuentemente una buena estrategia para usar en código con bucles de eventos. Por ejemplo, esta estrategia es empleada por `Gtk.jl` para gestionar el recuento de referencias de tiempo de vida. En este enfoque, no hacemos ningún trabajo explícito dentro del `finalizer`, y en su lugar lo añadimos a una cola para ejecutarlo en un momento más seguro. De hecho, el programador de tareas de Julia ya utiliza esto, por lo que definir el finalizador como `x -> @spawn do_cleanup(x)` es un ejemplo de este enfoque. Sin embargo, ten en cuenta que esto no controla en qué hilo se ejecuta `do_cleanup`, por lo que `do_cleanup` aún necesitaría adquirir un bloqueo. Eso no tiene que ser cierto si implementas tu propia cola, ya que puedes drenar explícitamente esa cola solo desde tu hilo.
