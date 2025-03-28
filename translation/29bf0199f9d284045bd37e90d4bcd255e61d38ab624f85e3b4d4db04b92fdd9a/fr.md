```
findmax(A; dims) -> (maxval, index)
```

Pour une entrée de tableau, renvoie la valeur et l'index du maximum sur les dimensions données. `NaN` est considéré comme supérieur à toutes les autres valeurs sauf `missing`.

# Exemples

```jldoctest
julia> A = [1.0 2; 3 4]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> findmax(A, dims=1)
([3.0 4.0], CartesianIndex{2}[CartesianIndex(2, 1) CartesianIndex(2, 2)])

julia> findmax(A, dims=2)
([2.0; 4.0;;], CartesianIndex{2}[CartesianIndex(1, 2); CartesianIndex(2, 2);;])
```
