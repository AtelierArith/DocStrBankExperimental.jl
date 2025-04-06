```
ldiv!(a::Number, B::AbstractArray)
```

Divide cada entrada en un arreglo `B` por un escalar `a` sobrescribiendo `B` en su lugar. Usa [`rdiv!`](@ref) para dividir el escalar desde la derecha.

# Ejemplos

```jldoctest
julia> B = [1.0 2.0; 3.0 4.0]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> ldiv!(2.0, B)
2×2 Matrix{Float64}:
 0.5  1.0
 1.5  2.0
```
