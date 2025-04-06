```
Threads.foreach(f, channel::Channel;
                schedule::Threads.AbstractSchedule=Threads.FairSchedule(),
                ntasks=Threads.threadpoolsize())
```

Similar a `foreach(f, channel)`, pero la iteración sobre `channel` y las llamadas a `f` se dividen entre `ntasks` tareas generadas por `Threads.@spawn`. Esta función esperará a que todas las tareas generadas internamente se completen antes de devolver.

Si `schedule isa FairSchedule`, `Threads.foreach` intentará generar tareas de una manera que permita al programador de Julia equilibrar más libremente la carga de trabajo entre los hilos. Este enfoque generalmente tiene un mayor costo por elemento, pero puede funcionar mejor que `StaticSchedule` en concurrencia con otras cargas de trabajo multihilo.

Si `schedule isa StaticSchedule`, `Threads.foreach` generará tareas de una manera que incurre en un menor costo por elemento que `FairSchedule`, pero es menos adecuada para el equilibrio de carga. Este enfoque puede ser más adecuado para cargas de trabajo uniformes y de grano fino, pero puede funcionar peor que `FairSchedule` en concurrencia con otras cargas de trabajo multihilo.

# Ejemplos

```julia-repl
julia> n = 20

julia> c = Channel{Int}(ch -> foreach(i -> put!(ch, i), 1:n), 1)

julia> d = Channel{Int}(n) do ch
           f = i -> put!(ch, i^2)
           Threads.foreach(f, c)
       end

julia> collect(d)
collect(d) = [1, 4, 9, 16, 25, 36, 49, 64, 81, 100, 121, 144, 169, 196, 225, 256, 289, 324, 361, 400]
```

!!! compat "Julia 1.6"
    Esta función requiere Julia 1.6 o posterior.

