```
union!(s::Union{AbstractSet,AbstractVector}, itrs...)
```

Construit l'[`union`](@ref) des ensembles passés et écrase `s` avec le résultat. Maintient l'ordre avec les tableaux.

!!! avertissement
    Le comportement peut être inattendu lorsque tout argument muté partage de la mémoire avec un autre argument.


# Exemples

```jldoctest
julia> a = Set([3, 4, 5]);

julia> union!(a, 1:2:7);

julia> a
Set{Int64} avec 5 éléments :
  5
  4
  7
  3
  1
```
