```
sortperm!(ix, A; alg::Algorithm=DEFAULT_UNSTABLE, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward, [dims::Integer])
```

Comme [`sortperm`](@ref), mais accepte un vecteur ou tableau d'index préalloué `ix` avec les mêmes `axes` que `A`. `ix` est initialisé pour contenir les valeurs `LinearIndices(A)`.

!!! avertissement
    Le comportement peut être inattendu lorsque tout argument muté partage de la mémoire avec un autre argument.


!!! compat "Julia 1.9"
    La méthode acceptant `dims` nécessite au moins Julia 1.9.


# Exemples

```jldoctest
julia> v = [3, 1, 2]; p = zeros(Int, 3);

julia> sortperm!(p, v); p
3-element Vector{Int64}:
 2
 3
 1

julia> v[p]
3-element Vector{Int64}:
 1
 2
 3

julia> A = [8 7; 5 6]; p = zeros(Int,2, 2);

julia> sortperm!(p, A; dims=1); p
2×2 Matrix{Int64}:
 2  4
 1  3

julia> sortperm!(p, A; dims=2); p
2×2 Matrix{Int64}:
 3  1
 2  4
```
