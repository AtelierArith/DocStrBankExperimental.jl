```
reverse(A; dims=:)
```

Inverse `A` le long de la dimension `dims`, qui peut être un entier (une seule dimension), un tuple d'entiers (un tuple de dimensions) ou `:` (inverse le long de toutes les dimensions, par défaut). Voir aussi [`reverse!`](@ref) pour une inversion en place.

# Exemples

```jldoctest
julia> b = Int64[1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> reverse(b, dims=2)
2×2 Matrix{Int64}:
 2  1
 4  3

julia> reverse(b)
2×2 Matrix{Int64}:
 4  3
 2  1
```

!!! compat "Julia 1.6"
    Avant Julia 1.6, seuls les `dims` à un seul entier sont pris en charge dans `reverse`.

