```
@time expr
@time "descripción" expr
```

Una macro para ejecutar una expresión, imprimiendo el tiempo que tomó ejecutarla, el número de asignaciones y el número total de bytes que su ejecución causó que se asignaran, antes de devolver el valor de la expresión. Cualquier tiempo gastado en recolección de basura (gc), compilando nuevo código, o recompilando código invalidado se muestra como un porcentaje. Cualquier conflicto de bloqueo donde un [`ReentrantLock`](@ref) tuvo que esperar se muestra como un conteo.

Opcionalmente, proporciona una cadena de descripción para imprimir antes del informe de tiempo.

En algunos casos, el sistema mirará dentro de la expresión `@time` y compilará parte del código llamado antes de que comience la ejecución de la expresión de nivel superior. Cuando eso sucede, parte del tiempo de compilación no se contará. Para incluir este tiempo, puedes ejecutar `@time @eval ...`.

Consulta también [`@showtime`](@ref), [`@timev`](@ref), [`@timed`](@ref), [`@elapsed`](@ref), [`@allocated`](@ref), y [`@allocations`](@ref).

!!! nota
    Para un benchmarking más serio, considera la macro `@btime` del paquete BenchmarkTools.jl que, entre otras cosas, evalúa la función múltiples veces para reducir el ruido.


!!! compat "Julia 1.8"
    La opción de agregar una descripción se introdujo en Julia 1.8.

    El tiempo de recompilación que se muestra por separado del tiempo de compilación se introdujo en Julia 1.8


!!! compat "Julia 1.11"
    El informe de cualquier conflicto de bloqueo se agregó en Julia 1.11.


```julia-repl
julia> x = rand(10,10);

julia> @time x * x;
  0.606588 segundos (2.19 M asignaciones: 116.555 MiB, 3.75% tiempo gc, 99.94% tiempo de compilación)

julia> @time x * x;
  0.000009 segundos (1 asignación: 896 bytes)

julia> @time begin
           sleep(0.3)
           1+1
       end
  0.301395 segundos (8 asignaciones: 336 bytes)
2

julia> @time "Un sueño de un segundo" sleep(1)
Un sueño de un segundo: 1.005750 segundos (5 asignaciones: 144 bytes)

julia> for loop in 1:3
            @time loop sleep(1)
        end
1: 1.006760 segundos (5 asignaciones: 144 bytes)
2: 1.001263 segundos (5 asignaciones: 144 bytes)
3: 1.003676 segundos (5 asignaciones: 144 bytes)
```
