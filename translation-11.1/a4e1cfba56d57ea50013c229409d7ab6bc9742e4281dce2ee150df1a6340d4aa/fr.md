```
@allocations
```

Une macro pour évaluer une expression, ignorer la valeur résultante et retourner plutôt le nombre total d'allocations pendant l'évaluation de l'expression.

Voir aussi [`@allocated`](@ref), [`@time`](@ref), [`@timev`](@ref), [`@timed`](@ref), et [`@elapsed`](@ref).

```julia-repl
julia> @allocations rand(10^6)
2
```

!!! compat "Julia 1.9"
    Cette macro a été ajoutée dans Julia 1.9.

