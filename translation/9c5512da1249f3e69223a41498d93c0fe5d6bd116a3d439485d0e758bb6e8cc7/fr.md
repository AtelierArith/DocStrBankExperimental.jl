```
setdiff!(s, itrs...)
```

Supprime de l'ensemble `s` (sur place) chaque élément de chaque itérable de `itrs`. Maintient l'ordre avec les tableaux.

!!! avertissement
    Le comportement peut être inattendu lorsque tout argument modifié partage de la mémoire avec un autre argument.


# Exemples

```jldoctest
julia> a = Set([1, 3, 4, 5]);

julia> setdiff!(a, 1:2:6);

julia> a
Set{Int64} with 1 element:
  4
```
