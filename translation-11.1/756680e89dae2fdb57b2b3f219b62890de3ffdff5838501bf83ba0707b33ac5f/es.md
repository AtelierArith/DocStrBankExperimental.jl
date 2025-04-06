```
ndims(A::AbstractArray) -> Integer
```

Devuelve el número de dimensiones de `A`.

Véase también: [`size`](@ref), [`axes`](@ref).

# Ejemplos

```jldoctest
julia> A = fill(1, (3,4,5));

julia> ndims(A)
3
```
