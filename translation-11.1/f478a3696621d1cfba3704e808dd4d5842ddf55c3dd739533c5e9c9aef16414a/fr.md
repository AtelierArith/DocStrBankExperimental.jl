```
getindex(A, inds...)
```

Retourne un sous-ensemble du tableau `A` tel que sélectionné par les indices `inds`.

Chaque indice peut être de n'importe quel [type d'indice supporté](@ref man-supported-index-types), tel qu'un [`Integer`](@ref), [`CartesianIndex`](@ref), [plage](@ref Base.AbstractRange), ou [tableau](@ref man-multi-dim-arrays) d'indices supportés. Un [:](@ref Base.Colon) peut être utilisé pour sélectionner tous les éléments le long d'une dimension spécifique, et un tableau booléen (par exemple un `Array{Bool}` ou un [`BitArray`](@ref)) peut être utilisé pour filtrer les éléments où l'indice correspondant est `true`.

Lorsque `inds` sélectionne plusieurs éléments, cette fonction retourne un tableau nouvellement alloué. Pour indexer plusieurs éléments sans faire de copie, utilisez [`view`](@ref) à la place.

Voir la section du manuel sur [l'indexation des tableaux](@ref man-array-indexing) pour plus de détails.

# Exemples

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> getindex(A, 1)
1

julia> getindex(A, [2, 1])
2-element Vector{Int64}:
 3
 1

julia> getindex(A, 2:4)
3-element Vector{Int64}:
 3
 2
 4

julia> getindex(A, 2, 1)
3

julia> getindex(A, CartesianIndex(2, 1))
3

julia> getindex(A, :, 2)
2-element Vector{Int64}:
 2
 4

julia> getindex(A, 2, :)
2-element Vector{Int64}:
 3
 4

julia> getindex(A, A .> 2)
2-element Vector{Int64}:
 3
 4
```
