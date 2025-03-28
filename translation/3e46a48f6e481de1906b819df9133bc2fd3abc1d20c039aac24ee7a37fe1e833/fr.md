```
findall(A)
```

Retourne un vecteur `I` des indices ou clés `true` de `A`. S'il n'y a pas d'éléments de `A`, retourne un tableau vide. Pour rechercher d'autres types de valeurs, passez un prédicat comme premier argument.

Les indices ou clés sont du même type que ceux retournés par [`keys(A)`](@ref) et [`pairs(A)`](@ref).

Voir aussi : [`findfirst`](@ref), [`searchsorted`](@ref).

# Exemples

```jldoctest
julia> A = [true, false, false, true]
4-element Vector{Bool}:
 1
 0
 0
 1

julia> findall(A)
2-element Vector{Int64}:
 1
 4

julia> A = [true false; false true]
2×2 Matrix{Bool}:
 1  0
 0  1

julia> findall(A)
2-element Vector{CartesianIndex{2}}:
 CartesianIndex(1, 1)
 CartesianIndex(2, 2)

julia> findall(falses(3))
Int64[]
```
