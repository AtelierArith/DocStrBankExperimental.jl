```
@allocated
```

Une macro pour évaluer une expression, en ignorant la valeur résultante, et en retournant plutôt le nombre total d'octets alloués lors de l'évaluation de l'expression.

Voir aussi [`@allocations`](@ref), [`@time`](@ref), [`@timev`](@ref), [`@timed`](@ref), et [`@elapsed`](@ref).

```julia-repl
julia> @allocated rand(10^6)
8000080
```
