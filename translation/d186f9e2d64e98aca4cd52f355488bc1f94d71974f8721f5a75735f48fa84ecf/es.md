```
@lock_conflicts
```

Una macro para evaluar una expresión, descartar el valor resultante y, en su lugar, devolver el número total de conflictos de bloqueo durante la evaluación, donde un intento de bloqueo en un [`ReentrantLock`](@ref) resultó en una espera porque el bloqueo ya estaba en uso.

Véase también [`@time`](@ref), [`@timev`](@ref) y [`@timed`](@ref).

```julia-repl
julia> @lock_conflicts begin
    l = ReentrantLock()
    Threads.@threads for i in 1:Threads.nthreads()
        lock(l) do
        sleep(1)
        end
    end
end
5
```

!!! compat "Julia 1.11"
    Esta macro se agregó en Julia 1.11.

