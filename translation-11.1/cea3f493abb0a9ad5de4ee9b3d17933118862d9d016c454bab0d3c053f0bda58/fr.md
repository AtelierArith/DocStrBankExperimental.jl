```
findprev(predicate::Function, A, i)
```

Trouve l'indice précédent avant ou incluant `i` d'un élément de `A` pour lequel `predicate` renvoie `true`, ou `nothing` si non trouvé. Cela fonctionne pour les tableaux, les chaînes de caractères et la plupart des autres collections qui supportent [`getindex`](@ref), [`keys(A)`](@ref), et [`nextind`](@ref).

Les indices sont du même type que ceux retournés par [`keys(A)`](@ref) et [`pairs(A)`](@ref).

# Exemples

```jldoctest
julia> A = [4, 6, 1, 2]
4-element Vector{Int64}:
 4
 6
 1
 2

julia> findprev(isodd, A, 1) # renvoie nothing, mais pas imprimé dans le REPL

julia> findprev(isodd, A, 3)
3

julia> A = [4 6; 1 2]
2×2 Matrix{Int64}:
 4  6
 1  2

julia> findprev(isodd, A, CartesianIndex(1, 2))
CartesianIndex(2, 1)

julia> findprev(isspace, "a b c", 3)
2
```
