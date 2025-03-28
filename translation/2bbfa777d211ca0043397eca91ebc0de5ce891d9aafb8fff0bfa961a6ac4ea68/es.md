```
strides(A)
```

Devuelve una tupla de los pasos de memoria en cada dimensión.

Véase también: [`stride`](@ref).

# Ejemplos

```jldoctest
julia> A = fill(1, (3,4,5));

julia> strides(A)
(1, 3, 12)
```
