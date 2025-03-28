```
<(x, y)
```

Opérateur de comparaison inférieur. Fait appel à [`isless`](@ref). En raison du comportement des valeurs NaN en virgule flottante, cet opérateur implémente un ordre partiel.

# Implémentation

Les nouveaux types avec un ordre partiel canonique devraient implémenter cette fonction pour deux arguments du nouveau type. Les types avec un ordre total canonique devraient implémenter [`isless`](@ref) à la place.

Voir aussi [`isunordered`](@ref).

# Exemples

```jldoctest
julia> 'a' < 'b'
true

julia> "abc" < "abd"
true

julia> 5 < 3
false
```
