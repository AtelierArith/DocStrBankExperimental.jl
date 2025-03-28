```
sortperm(A; alg::Algorithm=DEFAULT_UNSTABLE, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward, [dims::Integer])
```

Retourne un vecteur ou tableau de permutation `I` qui place `A[I]` dans l'ordre trié selon la dimension donnée. Si `A` a plus d'une dimension, alors l'argument clé `dims` doit être spécifié. L'ordre est spécifié en utilisant les mêmes mots-clés que [`sort!`](@ref). La permutation est garantie d'être stable même si l'algorithme de tri est instable : les indices des éléments égaux apparaîtront dans l'ordre croissant.

Voir aussi [`sortperm!`](@ref), [`partialsortperm`](@ref), [`invperm`](@ref), [`indexin`](@ref). Pour trier des tranches d'un tableau, référez-vous à [`sortslices`](@ref).

!!! compat "Julia 1.9"
    La méthode acceptant `dims` nécessite au moins Julia 1.9.


# Exemples

```jldoctest
julia> v = [3, 1, 2];

julia> p = sortperm(v)
3-element Vector{Int64}:
 2
 3
 1

julia> v[p]
3-element Vector{Int64}:
 1
 2
 3

julia> A = [8 7; 5 6]
2×2 Matrix{Int64}:
 8  7
 5  6

julia> sortperm(A, dims = 1)
2×2 Matrix{Int64}:
 2  4
 1  3

julia> sortperm(A, dims = 2)
2×2 Matrix{Int64}:
 3  1
 2  4
```
