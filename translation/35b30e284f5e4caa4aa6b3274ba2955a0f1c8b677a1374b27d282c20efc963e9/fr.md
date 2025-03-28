```
prepend!(a::Vector, collections...) -> collection
```

Insère les éléments de chaque `collections` au début de `a`.

Lorsque `collections` spécifie plusieurs collections, l'ordre est maintenu : les éléments de `collections[1]` apparaîtront le plus à gauche dans `a`, et ainsi de suite.

!!! compat "Julia 1.6"
    Spécifier plusieurs collections à préfixer nécessite au moins Julia 1.6.


# Exemples

```jldoctest
julia> prepend!([3], [1, 2])
3-element Vector{Int64}:
 1
 2
 3

julia> prepend!([6], [1, 2], [3, 4, 5])
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```
