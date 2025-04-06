# [Asynchronous Programming](@id man-asynchronous)

Cuando un programa necesita interactuar con el mundo exterior, por ejemplo, comunicándose con otra máquina a través de Internet, las operaciones en el programa pueden necesitar ocurrir en un orden impredecible. Supongamos que tu programa necesita descargar un archivo. Nos gustaría iniciar la operación de descarga, realizar otras operaciones mientras esperamos a que se complete, y luego reanudar el código que necesita el archivo descargado cuando esté disponible. Este tipo de escenario cae en el dominio de la programación asíncrona, a veces también referida como programación concurrente (ya que, conceptualmente, múltiples cosas están sucediendo al mismo tiempo).

Para abordar estos escenarios, Julia proporciona [`Task`](@ref) (también conocido por varios otros nombres, como corutinas simétricas, hilos ligeros, multitarea cooperativa o continuaciones de un solo uso). Cuando se designa un trabajo de computación (en la práctica, ejecutar una función particular) como un `4d61726b646f776e2e436f64652822222c20225461736b2229_40726566`, se vuelve posible interrumpirlo al cambiar a otro `4d61726b646f776e2e436f64652822222c20225461736b2229_40726566`. El `4d61726b646f776e2e436f64652822222c20225461736b2229_40726566` original puede reanudarse más tarde, momento en el cual continuará justo donde lo dejó. Al principio, esto puede parecer similar a una llamada de función. Sin embargo, hay dos diferencias clave. Primero, cambiar de tareas no utiliza ningún espacio, por lo que se pueden producir cambios de tarea sin consumir la pila de llamadas. Segundo, el cambio entre tareas puede ocurrir en cualquier orden, a diferencia de las llamadas de función, donde la función llamada debe terminar de ejecutarse antes de que el control regrese a la función que la llamó.

## Basic `Task` operations

Puedes pensar en un `Task` como un identificador para una unidad de trabajo computacional que se debe realizar. Tiene un ciclo de vida de crear-iniciar-ejecutar-finalizar. Los Tasks se crean llamando al constructor `Task` en una función de 0 argumentos para ejecutar, o utilizando el macro [`@task`](@ref):

```julia-repl
julia> t = @task begin; sleep(5); println("done"); end
Task (runnable) @0x00007f13a40c0eb0
```

`@task x` es equivalente a `Task(()->x)`.

Esta tarea esperará cinco segundos y luego imprimirá `hecho`. Sin embargo, aún no ha comenzado a ejecutarse. Podemos ejecutarla cuando estemos listos llamando a [`schedule`](@ref):

```julia-repl
julia> schedule(t);
```

Si intentas esto en el REPL, verás que `schedule` devuelve inmediatamente. Eso se debe a que simplemente agrega `t` a una cola interna de tareas para ejecutar. Luego, el REPL imprimirá el siguiente aviso y esperará más entrada. Esperar la entrada del teclado proporciona una oportunidad para que otras tareas se ejecuten, por lo que en ese momento `t` comenzará. `t` llama a [`sleep`](@ref), que establece un temporizador y detiene la ejecución. Si se han programado otras tareas, podrían ejecutarse en ese momento. Después de cinco segundos, el temporizador se activa y reinicia `t`, y verás `done` impreso. `t` ha terminado.

La función [`wait`](@ref) bloquea la tarea que la llama hasta que otra tarea finaliza. Así que, por ejemplo, si escribes

```julia-repl
julia> schedule(t); wait(t)
```

en lugar de solo llamar a `schedule`, verás una pausa de cinco segundos antes de que aparezca el siguiente aviso de entrada. Eso se debe a que el REPL está esperando a que `t` termine antes de continuar.

Es común querer crear una tarea y programarla de inmediato, por lo que se proporciona la macro [`@async`](@ref) para ese propósito – `@async x` es equivalente a `schedule(@task x)`.

## Communicating with Channels

En algunos problemas, las diversas piezas de trabajo requeridas no están naturalmente relacionadas por llamadas a funciones; no hay un "llamador" o "llamado" obvio entre los trabajos que deben realizarse. Un ejemplo es el problema del productor-consumidor, donde un procedimiento complejo está generando valores y otro procedimiento complejo los está consumiendo. El consumidor no puede simplemente llamar a una función de productor para obtener un valor, porque el productor puede tener más valores que generar y, por lo tanto, puede que aún no esté listo para devolver. Con tareas, el productor y el consumidor pueden ejecutarse tanto como lo necesiten, pasando valores de un lado a otro según sea necesario.

Julia proporciona un mecanismo [`Channel`](@ref) para resolver este problema. Un `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566` es una cola de espera de primero en entrar, primero en salir, que puede tener múltiples tareas leyendo y escribiendo en ella.

Definamos una tarea de productor, que produce valores a través de la llamada [`put!`](@ref). Para consumir valores, necesitamos programar el productor para que se ejecute en una nueva tarea. Se puede utilizar un constructor especial [`Channel`](@ref) que acepta una función de 1 argumento como argumento para ejecutar una tarea vinculada a un canal. Luego podemos [`take!`](@ref) valores repetidamente desde el objeto del canal:

```jldoctest producer
julia> function producer(c::Channel)
           put!(c, "start")
           for n=1:4
               put!(c, 2n)
           end
           put!(c, "stop")
       end;

julia> chnl = Channel(producer);

julia> take!(chnl)
"start"

julia> take!(chnl)
2

julia> take!(chnl)
4

julia> take!(chnl)
6

julia> take!(chnl)
8

julia> take!(chnl)
"stop"
```

Una forma de pensar en este comportamiento es que `producer` pudo devolver múltiples veces. Entre las llamadas a [`put!`](@ref), la ejecución del productor está suspendida y el consumidor tiene el control.

El [`Channel`](@ref) devuelto se puede usar como un objeto iterable en un bucle `for`, en cuyo caso la variable del bucle toma todos los valores producidos. El bucle se termina cuando el canal se cierra.

```jldoctest producer
julia> for x in Channel(producer)
           println(x)
       end
start
2
4
6
8
stop
```

Tenga en cuenta que no tuvimos que cerrar explícitamente el canal en el productor. Esto se debe a que el acto de vincular un [`Channel`](@ref) a un [`Task`](@ref) asocia la duración de apertura de un canal con la de la tarea vinculada. El objeto canal se cierra automáticamente cuando la tarea termina. Se pueden vincular múltiples canales a una tarea, y viceversa.

Mientras que el constructor [`Task`](@ref) espera una función sin argumentos, el método [`Channel`](@ref) que crea un canal vinculado a una tarea espera una función que acepte un solo argumento de tipo `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566`. Un patrón común es que el productor esté parametrizado, en cuyo caso se necesita una aplicación parcial de función para crear una función con 0 o 1 argumento [anonymous function](@ref man-anonymous-functions).

Para [`Task`](@ref) objetos, esto se puede hacer directamente o mediante el uso de una macro de conveniencia:

```julia
function mytask(myarg)
    ...
end

taskHdl = Task(() -> mytask(7))
# or, equivalently
taskHdl = @task mytask(7)
```

Para orquestar patrones de distribución de trabajo más avanzados, [`bind`](@ref) y [`schedule`](@ref) se pueden usar en conjunto con [`Task`](@ref) y [`Channel`](@ref) constructores para vincular explícitamente un conjunto de canales con un conjunto de tareas de productor/consumidor.

### More on Channels

Un canal se puede visualizar como un tubo, es decir, tiene un extremo de escritura y un extremo de lectura:

  * Múltiples escritores en diferentes tareas pueden escribir en el mismo canal de manera concurrente a través de llamadas [`put!`](@ref).
  * Múltiples lectores en diferentes tareas pueden leer datos de manera concurrente a través de [`take!`](@ref) llamadas.
  * Como ejemplo:

    ```julia
    # Given Channels c1 and c2,
    c1 = Channel(32)
    c2 = Channel(32)

    # and a function `foo` which reads items from c1, processes the item read
    # and writes a result to c2,
    function foo()
        while true
            data = take!(c1)
            [...]               # process data
            put!(c2, result)    # write out result
        end
    end

    # we can schedule `n` instances of `foo` to be active concurrently.
    for _ in 1:n
        errormonitor(@async foo())
    end
    ```
  * Los canales se crean a través del constructor `Channel{T}(sz)`. El canal solo contendrá objetos del tipo `T`. Si el tipo no se especifica, el canal puede contener objetos de cualquier tipo. `sz` se refiere al número máximo de elementos que se pueden mantener en el canal en cualquier momento. Por ejemplo, `Channel(32)` crea un canal que puede contener un máximo de 32 objetos de cualquier tipo. Un `Channel{MyType}(64)` puede contener hasta 64 objetos de `MyType` en cualquier momento.
  * Si un [`Channel`](@ref) está vacío, los lectores (en una llamada a [`take!`](@ref)) se bloquearán hasta que los datos estén disponibles.
  * Si un [`Channel`](@ref) está lleno, los escritores (en una llamada a [`put!`](@ref)) se bloquearán hasta que haya espacio disponible.
  * [`isready`](@ref) prueba la presencia de cualquier objeto en el canal, mientras que [`wait`](@ref) espera a que un objeto esté disponible.
  * Un [`Channel`](@ref) está en un estado abierto inicialmente. Esto significa que se puede leer y escribir libremente a través de llamadas [`take!`](@ref) y [`put!`](@ref). [`close`](@ref) cierra un `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566`. En un `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566` cerrado, `4d61726b646f776e2e436f64652822222c2022707574212229_40726566` fallará. Por ejemplo:

    ```julia-repl
    julia> c = Channel(2);

    julia> put!(c, 1) # `put!` on an open channel succeeds
    1

    julia> close(c);

    julia> put!(c, 2) # `put!` on a closed channel throws an exception.
    ERROR: InvalidStateException: Channel is closed.
    Stacktrace:
    [...]
    ```
  * [`take!`](@ref) y [`fetch`](@ref) (que recupera pero no elimina el valor) en un canal cerrado devuelve con éxito cualquier valor existente hasta que se vacíe. Continuando con el ejemplo anterior:

    ```julia-repl
    julia> fetch(c) # Any number of `fetch` calls succeed.
    1

    julia> fetch(c)
    1

    julia> take!(c) # The first `take!` removes the value.
    1

    julia> take!(c) # No more data available on a closed channel.
    ERROR: InvalidStateException: Channel is closed.
    Stacktrace:
    [...]
    ```

Considere un ejemplo simple utilizando canales para la comunicación entre tareas. Iniciamos 4 tareas para procesar datos de un único canal `jobs`. Los trabajos, identificados por un id (`job_id`), se escriben en el canal. Cada tarea en esta simulación lee un `job_id`, espera un tiempo aleatorio y escribe de vuelta una tupla de `job_id` y el tiempo simulado en el canal de resultados. Finalmente, se imprimen todos los `resultados`.

```julia-repl
julia> const jobs = Channel{Int}(32);

julia> const results = Channel{Tuple}(32);

julia> function do_work()
           for job_id in jobs
               exec_time = rand()
               sleep(exec_time)                # simulates elapsed time doing actual work
                                               # typically performed externally.
               put!(results, (job_id, exec_time))
           end
       end;

julia> function make_jobs(n)
           for i in 1:n
               put!(jobs, i)
           end
       end;

julia> n = 12;

julia> errormonitor(@async make_jobs(n)); # feed the jobs channel with "n" jobs

julia> for i in 1:4 # start 4 tasks to process requests in parallel
           errormonitor(@async do_work())
       end

julia> @elapsed while n > 0 # print out results
           job_id, exec_time = take!(results)
           println("$job_id finished in $(round(exec_time; digits=2)) seconds")
           global n = n - 1
       end
4 finished in 0.22 seconds
3 finished in 0.45 seconds
1 finished in 0.5 seconds
7 finished in 0.14 seconds
2 finished in 0.78 seconds
5 finished in 0.9 seconds
9 finished in 0.36 seconds
6 finished in 0.87 seconds
8 finished in 0.79 seconds
10 finished in 0.64 seconds
12 finished in 0.5 seconds
11 finished in 0.97 seconds
0.029772311
```

En lugar de `errormonitor(t)`, una solución más robusta puede ser usar `bind(results, t)`, ya que eso no solo registrará cualquier fallo inesperado, sino que también forzará el cierre de los recursos asociados y propagará la excepción en todas partes.

## More task operations

Las operaciones de tarea se basan en un primitivo de bajo nivel llamado [`yieldto`](@ref). `yieldto(task, value)` suspende la tarea actual, cambia a la `task` especificada y hace que la última llamada a `4d61726b646f776e2e436f64652822222c20227969656c64746f2229_40726566` de esa tarea devuelva el `value` especificado. Nota que `4d61726b646f776e2e436f64652822222c20227969656c64746f2229_40726566` es la única operación requerida para usar el flujo de control estilo tarea; en lugar de llamar y devolver, siempre estamos cambiando a una tarea diferente. Por eso, esta característica también se llama "corutinas simétricas"; cada tarea se cambia hacia y desde utilizando el mismo mecanismo.

[`yieldto`](@ref) es poderoso, pero la mayoría de los usos de tareas no lo invocan directamente. Considera por qué podría ser esto. Si cambias de la tarea actual, probablemente querrás volver a ella en algún momento, pero saber cuándo volver y saber qué tarea tiene la responsabilidad de volver puede requerir una coordinación considerable. Por ejemplo, [`put!`](@ref) y [`take!`](@ref) son operaciones bloqueantes, que, cuando se utilizan en el contexto de canales, mantienen el estado para recordar quiénes son los consumidores. No necesitar llevar un seguimiento manual de la tarea consumidora es lo que hace que `4d61726b646f776e2e436f64652822222c2022707574212229_40726566` sea más fácil de usar que el bajo nivel `4d61726b646f776e2e436f64652822222c20227969656c64746f2229_40726566`.

Además de [`yieldto`](@ref), se necesitan algunas otras funciones básicas para utilizar las tareas de manera efectiva.

  * [`current_task`](@ref) obtiene una referencia a la tarea que se está ejecutando actualmente.
  * [`istaskdone`](@ref) consulta si una tarea ha salido.
  * [`istaskstarted`](@ref) consulta si una tarea ya se ha ejecutado.
  * [`task_local_storage`](@ref) manipula un almacén de clave-valor específico para la tarea actual.

## Tasks and events

La mayoría de los cambios de tarea ocurren como resultado de esperar eventos como solicitudes de E/S, y son realizados por un programador incluido en Julia Base. El programador mantiene una cola de tareas ejecutables y ejecuta un bucle de eventos que reinicia tareas basadas en eventos externos como la llegada de mensajes.

The basic function for waiting for an event is [`wait`](@ref). Several objects implement [`wait`](@ref); for example, given a `Process` object, [`wait`](@ref) will wait for it to exit. [`wait`](@ref) is often implicit; for example, a [`wait`](@ref) can happen inside a call to [`read`](@ref) to wait for data to be available.

En todos estos casos, [`wait`](@ref) opera en última instancia sobre un objeto [`Condition`](@ref), que se encarga de encolar y reiniciar tareas. Cuando una tarea llama a `4d61726b646f776e2e436f64652822222c2022776169742229_40726566` en un `4d61726b646f776e2e436f64652822222c2022436f6e646974696f6e2229_40726566`, la tarea se marca como no ejecutable, se añade a la cola de condiciones y se cambia al programador. El programador luego seleccionará otra tarea para ejecutar o se bloqueará esperando eventos externos. Si todo va bien, eventualmente un controlador de eventos llamará a [`notify`](@ref) en la condición, lo que hace que las tareas que esperan esa condición se vuelvan ejecutables nuevamente.

Una tarea creada explícitamente al llamar a [`Task`](@ref) inicialmente no es conocida por el programador. Esto te permite gestionar tareas manualmente usando [`yieldto`](@ref) si lo deseas. Sin embargo, cuando tal tarea espera un evento, aún se reinicia automáticamente cuando ocurre el evento, como cabría esperar.
