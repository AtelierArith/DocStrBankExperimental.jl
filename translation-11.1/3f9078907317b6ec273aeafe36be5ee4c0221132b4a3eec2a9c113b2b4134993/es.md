```
@allocated
```

Una macro para evaluar una expresión, descartando el valor resultante, en su lugar devolviendo el número total de bytes asignados durante la evaluación de la expresión.

Véase también [`@allocations`](@ref), [`@time`](@ref), [`@timev`](@ref), [`@timed`](@ref), y [`@elapsed`](@ref).

```julia-repl
julia> @allocated rand(10^6)
8000080
```
