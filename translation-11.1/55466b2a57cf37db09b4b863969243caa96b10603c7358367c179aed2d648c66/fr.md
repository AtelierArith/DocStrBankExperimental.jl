```
argmax(A; dims) -> indices
```

Pour une entrée de tableau, renvoie les indices des éléments maximaux sur les dimensions données. `NaN` est considéré comme supérieur à toutes les autres valeurs sauf `missing`.

# Exemples

```jldoctest
julia> A = [1.0 2; 3 4]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> argmax(A, dims=1)
1×2 Matrix{CartesianIndex{2}}:
 CartesianIndex(2, 1)  CartesianIndex(2, 2)

julia> argmax(A, dims=2)
2×1 Matrix{CartesianIndex{2}}:
 CartesianIndex(1, 2)
 CartesianIndex(2, 2)
```
