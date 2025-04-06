```
selectdim(A, d::Integer, i)
```

Renvoie une vue de toutes les données de `A` où l'index pour la dimension `d` est égal à `i`.

Équivalent à `view(A,:,:,...,i,:,:,...)` où `i` est en position `d`.

Voir aussi : [`eachslice`](@ref).

# Exemples

```jldoctest
julia> A = [1 2 3 4; 5 6 7 8]
2×4 Matrix{Int64}:
 1  2  3  4
 5  6  7  8

julia> selectdim(A, 2, 3)
2-element view(::Matrix{Int64}, :, 3) with eltype Int64:
 3
 7

julia> selectdim(A, 2, 3:4)
2×2 view(::Matrix{Int64}, :, 3:4) with eltype Int64:
 3  4
 7  8
```
