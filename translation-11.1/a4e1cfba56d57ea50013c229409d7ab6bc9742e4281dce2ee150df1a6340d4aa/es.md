```
@allocations
```

Una macro para evaluar una expresión, descartar el valor resultante y, en su lugar, devolver el número total de asignaciones durante la evaluación de la expresión.

Véase también [`@allocated`](@ref), [`@time`](@ref), [`@timev`](@ref), [`@timed`](@ref) y [`@elapsed`](@ref).

```julia-repl
julia> @allocations rand(10^6)
2
```

!!! compat "Julia 1.9"
    Esta macro se agregó en Julia 1.9.

