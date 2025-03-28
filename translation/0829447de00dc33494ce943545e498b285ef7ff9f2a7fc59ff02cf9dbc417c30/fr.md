```
sort!(A; dims::Integer, alg::Algorithm=defalg(A), lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

Trie le tableau multidimensionnel `A` le long de la dimension `dims`. Voir la version unidimensionnelle de [`sort!`](@ref) pour une description des arguments de mot-clé possibles.

Pour trier des tranches d'un tableau, référez-vous à [`sortslices`](@ref).

!!! compat "Julia 1.1"
    Cette fonction nécessite au moins Julia 1.1.


# Exemples

```jldoctest
julia> A = [4 3; 1 2]
2×2 Matrix{Int64}:
 4  3
 1  2

julia> sort!(A, dims = 1); A
2×2 Matrix{Int64}:
 1  2
 4  3

julia> sort!(A, dims = 2); A
2×2 Matrix{Int64}:
 1  2
 3  4
```
