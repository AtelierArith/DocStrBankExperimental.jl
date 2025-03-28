```
findprev(A, i)
```

Trouver l'indice précédent avant ou incluant `i` d'un élément `true` de `A`, ou `nothing` s'il n'est pas trouvé.

Les indices sont du même type que ceux retournés par [`keys(A)`](@ref) et [`pairs(A)`](@ref).

Voir aussi : [`findnext`](@ref), [`findfirst`](@ref), [`findall`](@ref).

# Exemples

```jldoctest
julia> A = [false, false, true, true]
4-element Vector{Bool}:
 0
 0
 1
 1

julia> findprev(A, 3)
3

julia> findprev(A, 1) # retourne nothing, mais n'est pas affiché dans le REPL

julia> A = [false false; true true]
2×2 Matrix{Bool}:
 0  0
 1  1

julia> findprev(A, CartesianIndex(2, 1))
CartesianIndex(2, 1)
```
