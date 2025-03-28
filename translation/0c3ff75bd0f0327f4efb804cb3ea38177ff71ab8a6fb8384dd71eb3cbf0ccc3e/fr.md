```
findnext(A, i)
```

Trouver l'index suivant après ou incluant `i` d'un élément `true` de `A`, ou `nothing` si non trouvé.

Les indices sont du même type que ceux retournés par [`keys(A)`](@ref) et [`pairs(A)`](@ref).

# Exemples

```jldoctest
julia> A = [false, false, true, false]
4-element Vector{Bool}:
 0
 0
 1
 0

julia> findnext(A, 1)
3

julia> findnext(A, 4) # retourne nothing, mais n'est pas affiché dans le REPL

julia> A = [false false; true false]
2×2 Matrix{Bool}:
 0  0
 1  0

julia> findnext(A, CartesianIndex(1, 1))
CartesianIndex(2, 1)
```
