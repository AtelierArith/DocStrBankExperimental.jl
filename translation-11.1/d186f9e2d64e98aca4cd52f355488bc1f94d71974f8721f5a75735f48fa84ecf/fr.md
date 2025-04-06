```
@lock_conflicts
```

Une macro pour évaluer une expression, ignorer la valeur résultante et retourner plutôt le nombre total de conflits de verrouillage pendant l'évaluation, où une tentative de verrouillage sur un [`ReentrantLock`](@ref) a entraîné une attente parce que le verrou était déjà détenu.

Voir aussi [`@time`](@ref), [`@timev`](@ref) et [`@timed`](@ref).

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
    Cette macro a été ajoutée dans Julia 1.11.

