```
findfirst(predicate::Function, A)
```

Renvoie l'indice ou la clé du premier élément de `A` pour lequel `predicate` renvoie `true`. Renvoie `nothing` s'il n'y a pas un tel élément.

Les indices ou clés sont du même type que ceux renvoyés par [`keys(A)`](@ref) et [`pairs(A)`](@ref).

# Exemples

```jldoctest
julia> A = [1, 4, 2, 2]
4-element Vector{Int64}:
 1
 4
 2
 2

julia> findfirst(iseven, A)
2

julia> findfirst(x -> x>10, A) # renvoie nothing, mais n'est pas affiché dans le REPL

julia> findfirst(isequal(4), A)
2

julia> A = [1 4; 2 2]
2×2 Matrix{Int64}:
 1  4
 2  2

julia> findfirst(iseven, A)
CartesianIndex(2, 1)
```
