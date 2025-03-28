```
svdvals(A, B)
```

Devuelve los valores singulares generalizados de la descomposición en valores singulares generalizados de `A` y `B`. Ver también [`svd`](@ref).

# Ejemplos

```jldoctest
julia> A = [1. 0.; 0. -1.]
2×2 Matrix{Float64}:
 1.0   0.0
 0.0  -1.0

julia> B = [0. 1.; 1. 0.]
2×2 Matrix{Float64}:
 0.0  1.0
 1.0  0.0

julia> svdvals(A, B)
2-element Vector{Float64}:
 1.0
 1.0
```
