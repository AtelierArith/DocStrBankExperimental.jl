```
rdiv!(A::AbstractArray, b::Number)
```

Divide cada entrada en un arreglo `A` por un escalar `b` sobrescribiendo `A` en su lugar. Usa [`ldiv!`](@ref) para dividir el escalar desde la izquierda.

# Ejemplos

```jldoctest
julia> A = [1.0 2.0; 3.0 4.0]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> rdiv!(A, 2.0)
2×2 Matrix{Float64}:
 0.5  1.0
 1.5  2.0
```
