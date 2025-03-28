```
cumprod(A; dims::Integer)
```

Produit cumulatif le long de la dimension `dim`. Voir aussi [`cumprod!`](@ref) pour utiliser un tableau de sortie préalloué, à la fois pour des performances et pour contrôler la précision de la sortie (par exemple, pour éviter le débordement).

# Exemples

```jldoctest
julia> a = Int8[1 2 3; 4 5 6];

julia> cumprod(a, dims=1)
2×3 Matrix{Int64}:
 1   2   3
 4  10  18

julia> cumprod(a, dims=2)
2×3 Matrix{Int64}:
 1   2    6
 4  20  120
```
