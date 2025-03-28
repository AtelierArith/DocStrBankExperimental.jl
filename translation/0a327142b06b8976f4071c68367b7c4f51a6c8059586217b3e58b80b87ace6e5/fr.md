```
findnext(predicate::Function, A, i)
```

Trouve l'index suivant après ou incluant `i` d'un élément de `A` pour lequel `predicate` renvoie `true`, ou `nothing` si non trouvé. Cela fonctionne pour les tableaux, les chaînes de caractères et la plupart des autres collections qui supportent [`getindex`](@ref), [`keys(A)`](@ref), et [`nextind`](@ref).

Les indices sont du même type que ceux retournés par [`keys(A)`](@ref) et [`pairs(A)`](@ref).

# Exemples

```jldoctest
julia> A = [1, 4, 2, 2];

julia> findnext(isodd, A, 1)
1

julia> findnext(isodd, A, 2) # renvoie nothing, mais n'est pas imprimé dans le REPL

julia> A = [1 4; 2 2];

julia> findnext(isodd, A, CartesianIndex(1, 1))
CartesianIndex(1, 1)

julia> findnext(isspace, "a b c", 3)
4
```
