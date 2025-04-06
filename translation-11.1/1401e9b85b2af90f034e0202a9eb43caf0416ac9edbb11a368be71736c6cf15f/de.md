```
svdvals(A, B)
```

Gibt die verallgemeinerten singulären Werte aus der verallgemeinerten singulären Wertzerlegung von `A` und `B` zurück. Siehe auch [`svd`](@ref).

# Beispiele

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
