```
sort(A; dims::Integer, alg::Algorithm=defalg(A), lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

Trie un tableau multidimensionnel `A` le long de la dimension donnée. Voir [`sort!`](@ref) pour une description des arguments de mot-clé possibles.

Pour trier des tranches d'un tableau, référez-vous à [`sortslices`](@ref).

# Exemples

```jldoctest
julia> A = [4 3; 1 2]
2×2 Matrix{Int64}:
 4  3
 1  2

julia> sort(A, dims = 1)
2×2 Matrix{Int64}:
 1  2
 4  3

julia> sort(A, dims = 2)
2×2 Matrix{Int64}:
 3  4
 1  2
```
