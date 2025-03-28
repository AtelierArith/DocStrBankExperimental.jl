```
findfirst(A)
```

Renvoie l'index ou la clé de la première valeur `true` dans `A`. Renvoie `nothing` si aucune valeur de ce type n'est trouvée. Pour rechercher d'autres types de valeurs, passez un prédicat comme premier argument.

Les indices ou clés sont du même type que ceux retournés par [`keys(A)`](@ref) et [`pairs(A)`](@ref).

Voir aussi : [`findall`](@ref), [`findnext`](@ref), [`findlast`](@ref), [`searchsortedfirst`](@ref).

# Exemples

```jldoctest
julia> A = [false, false, true, false]
4-element Vector{Bool}:
 0
 0
 1
 0

julia> findfirst(A)
3

julia> findfirst(falses(3)) # renvoie nothing, mais n'est pas affiché dans le REPL

julia> A = [false false; true false]
2×2 Matrix{Bool}:
 0  0
 1  0

julia> findfirst(A)
CartesianIndex(2, 1)
```
