```
findlast(predicate::Function, A)
```

Retourne l'indice ou la clé du dernier élément de `A` pour lequel `predicate` retourne `true`. Retourne `nothing` s'il n'y a pas un tel élément.

Les indices ou clés sont du même type que ceux retournés par [`keys(A)`](@ref) et [`pairs(A)`](@ref).

# Exemples

```jldoctest
julia> A = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> findlast(isodd, A)
3

julia> findlast(x -> x > 5, A) # retourne nothing, mais n'est pas affiché dans le REPL

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> findlast(isodd, A)
CartesianIndex(2, 1)
```
