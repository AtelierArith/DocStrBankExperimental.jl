```
findmin(A; dims) -> (minval, index)
```

Pour une entrée de tableau, renvoie la valeur et l'index du minimum sur les dimensions données. `NaN` est considéré comme inférieur à toutes les autres valeurs sauf `missing`.

# Exemples

```jldoctest
julia> A = [1.0 2; 3 4]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> findmin(A, dims=1)
([1.0 2.0], CartesianIndex{2}[CartesianIndex(1, 1) CartesianIndex(1, 2)])

julia> findmin(A, dims=2)
([1.0; 3.0;;], CartesianIndex{2}[CartesianIndex(1, 1); CartesianIndex(2, 1);;])
```
