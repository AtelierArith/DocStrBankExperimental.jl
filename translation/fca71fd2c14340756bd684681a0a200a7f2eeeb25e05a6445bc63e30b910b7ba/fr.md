```
allunique(itr) -> Bool
allunique(f, itr) -> Bool
```

Retourne `true` si toutes les valeurs de `itr` sont distinctes lorsqu'elles sont comparées avec [`isequal`](@ref). Ou si toutes les valeurs de `[f(x) for x in itr]` sont distinctes, pour la deuxième méthode.

Notez que `allunique(f, itr)` peut appeler `f` moins de fois que `length(itr)`. Le nombre précis d'appels est considéré comme un détail d'implémentation.

`allunique` peut utiliser une implémentation spécialisée lorsque l'entrée est triée.

Voir aussi : [`unique`](@ref), [`issorted`](@ref), [`allequal`](@ref).

!!! compat "Julia 1.11"
    La méthode `allunique(f, itr)` nécessite au moins Julia 1.11.


# Exemples

```jldoctest
julia> allunique([1, 2, 3])
true

julia> allunique([1, 2, 1, 2])
false

julia> allunique(Real[1, 1.0, 2])
false

julia> allunique([NaN, 2.0, NaN, 4.0])
false

julia> allunique(abs, [1, -1, 2])
false
```
