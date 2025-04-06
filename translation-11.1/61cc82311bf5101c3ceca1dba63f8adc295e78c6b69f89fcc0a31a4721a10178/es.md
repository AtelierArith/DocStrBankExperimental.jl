```
Threads.@threads [schedule] for ... end
```

Una macro para ejecutar un bucle `for` en paralelo. El espacio de iteración se distribuye a tareas de gran grano. Esta política se puede especificar mediante el argumento `schedule`. La ejecución del bucle espera la evaluación de todas las iteraciones.

Véase también: [`@spawn`](@ref Threads.@spawn) y `pmap` en [`Distributed`](@ref man-distributed).

# Ayuda extendida

## Semántica

A menos que se especifiquen garantías más fuertes mediante la opción de programación, el bucle ejecutado por la macro `@threads` tiene la siguiente semántica.

La macro `@threads` ejecuta el cuerpo del bucle en un orden no especificado y potencialmente de manera concurrente. No especifica las asignaciones exactas de las tareas y los hilos de trabajo. Las asignaciones pueden ser diferentes para cada ejecución. El código del cuerpo del bucle (incluido cualquier código llamado de manera transitiva desde él) no debe hacer suposiciones sobre la distribución de iteraciones a tareas o el hilo de trabajo en el que se ejecutan. El cuerpo del bucle para cada iteración debe ser capaz de avanzar de manera independiente de otras iteraciones y estar libre de condiciones de carrera. Como tal, las sincronizaciones inválidas entre iteraciones pueden provocar un bloqueo, mientras que los accesos a memoria no sincronizados pueden resultar en un comportamiento indefinido.

Por ejemplo, las condiciones anteriores implican que:

  * Un bloqueo tomado en una iteración *debe* ser liberado dentro de la misma iteración.
  * Comunicar entre iteraciones utilizando primitivas de bloqueo como `Channel`s es incorrecto.
  * Escribir solo en ubicaciones no compartidas entre iteraciones (a menos que se use un bloqueo o una operación atómica).
  * A menos que se use la programación `:static`, el valor de [`threadid()`](@ref Threads.threadid) puede cambiar incluso dentro de una sola iteración. Véase [`Migración de Tareas`](@ref man-task-migration).

## Programadores

Sin el argumento del programador, la programación exacta no está especificada y varía entre las versiones de Julia. Actualmente, se utiliza `:dynamic` cuando no se especifica el programador.

!!! compat "Julia 1.5"
    El argumento `schedule` está disponible a partir de Julia 1.5.


### `:dynamic` (predeterminado)

El programador `:dynamic` ejecuta iteraciones dinámicamente en los hilos de trabajo disponibles. La implementación actual asume que la carga de trabajo para cada iteración es uniforme. Sin embargo, esta suposición puede eliminarse en el futuro.

Esta opción de programación es meramente una sugerencia para el mecanismo de ejecución subyacente. Sin embargo, se pueden esperar algunas propiedades. El número de `Task`s utilizados por el programador `:dynamic` está limitado por un pequeño múltiplo constante del número de hilos de trabajo disponibles ([`Threads.threadpoolsize()`](@ref)). Cada tarea procesa regiones contiguas del espacio de iteración. Por lo tanto, `@threads :dynamic for x in xs; f(x); end` es típicamente más eficiente que `@sync for x in xs; @spawn f(x); end` si `length(xs)` es significativamente mayor que el número de hilos de trabajo y el tiempo de ejecución de `f(x)` es relativamente menor que el costo de crear y sincronizar una tarea (típicamente menos de 10 microsegundos).

!!! compat "Julia 1.8"
    La opción `:dynamic` para el argumento `schedule` está disponible y es la predeterminada a partir de Julia 1.8.


### `:greedy`

El programador `:greedy` genera hasta [`Threads.threadpoolsize()`](@ref) tareas, cada una trabajando de manera codiciosa en los valores iterados dados a medida que se producen. Tan pronto como una tarea termina su trabajo, toma el siguiente valor del iterador. El trabajo realizado por cualquier tarea individual no necesariamente se realiza en valores contiguos del iterador. El iterador dado puede producir valores indefinidamente, solo se requiere la interfaz del iterador (sin indexación).

Esta opción de programación es generalmente una buena elección si la carga de trabajo de las iteraciones individuales no es uniforme/tiene una gran dispersión.

!!! compat "Julia 1.11"
    La opción `:greedy` para el argumento `schedule` está disponible a partir de Julia 1.11.


### `:static`

El programador `:static` crea una tarea por hilo y divide las iteraciones de manera equitativa entre ellas, asignando cada tarea específicamente a cada hilo. En particular, el valor de [`threadid()`](@ref Threads.threadid) está garantizado que sea constante dentro de una iteración. Es un error especificar `:static` si se usa desde dentro de otro bucle `@threads` o desde un hilo diferente al 1.

!!! note
    La programación `:static` existe para apoyar la transición de código escrito antes de Julia 1.3. En las funciones de biblioteca recién escritas, se desaconseja la programación `:static` porque las funciones que utilizan esta opción no pueden ser llamadas desde hilos de trabajo arbitrarios.


## Ejemplos

Para ilustrar las diferentes estrategias de programación, considere la siguiente función `busywait` que contiene un bucle de tiempo que no cede y que se ejecuta durante un número dado de segundos.

```julia-repl
julia> function busywait(seconds)
            tstart = time_ns()
            while (time_ns() - tstart) / 1e9 < seconds
            end
        end

julia> @time begin
            Threads.@spawn busywait(5)
            Threads.@threads :static for i in 1:Threads.threadpoolsize()
                busywait(1)
            end
        end
6.003001 seconds (16.33 k allocations: 899.255 KiB, 0.25% compilation time)

julia> @time begin
            Threads.@spawn busywait(5)
            Threads.@threads :dynamic for i in 1:Threads.threadpoolsize()
                busywait(1)
            end
        end
2.012056 seconds (16.05 k allocations: 883.919 KiB, 0.66% compilation time)
```

El ejemplo `:dynamic` toma 2 segundos ya que uno de los hilos no ocupados puede ejecutar dos de las iteraciones de 1 segundo para completar el bucle `for`. ```
