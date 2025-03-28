```
filter(f, a)
```

Renvoie une copie de la collection `a`, en supprimant les éléments pour lesquels `f` est `false`. La fonction `f` reçoit un argument.

!!! compat "Julia 1.4"
    Le support de `a` en tant que tuple nécessite au moins Julia 1.4.


Voir aussi : [`filter!`](@ref), [`Iterators.filter`](@ref).

# Exemples

```jldoctest
julia> a = 1:10
1:10

julia> filter(isodd, a)
5-element Vector{Int64}:
 1
 3
 5
 7
 9
```
