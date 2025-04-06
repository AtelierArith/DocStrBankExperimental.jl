```
findlast(A)
```

Renvoie l'indice ou la clé de la dernière valeur `true` dans `A`. Renvoie `nothing` s'il n'y a pas de valeur `true` dans `A`.

Les indices ou clés sont du même type que ceux retournés par [`keys(A)`](@ref) et [`pairs(A)`](@ref).

Voir aussi : [`findfirst`](@ref), [`findprev`](@ref), [`findall`](@ref).

# Exemples

```jldoctest
julia> A = [true, false, true, false]
4-element Vector{Bool}:
 1
 0
 1
 0

julia> findlast(A)
3

julia> A = falses(2,2);

julia> findlast(A) # renvoie nothing, mais pas affiché dans le REPL

julia> A = [true false; true false]
2×2 Matrix{Bool}:
 1  0
 1  0

julia> findlast(A)
CartesianIndex(2, 1)
```
