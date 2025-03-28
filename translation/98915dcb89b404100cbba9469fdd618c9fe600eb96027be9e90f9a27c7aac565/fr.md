```
!=(x, y)
≠(x,y)
```

Opérateur de comparaison non égal. Donne toujours la réponse opposée à [`==`](@ref).

# Implémentation

Les nouveaux types ne devraient généralement pas implémenter cela, et s'appuyer sur la définition par défaut `!=(x,y) = !(x==y)` à la place.

# Exemples

```jldoctest
julia> 3 != 2
true

julia> "foo" ≠ "foo"
false
```
