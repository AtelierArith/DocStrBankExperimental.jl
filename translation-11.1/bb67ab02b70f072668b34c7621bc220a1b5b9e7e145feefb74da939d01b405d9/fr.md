```
allequal(itr) -> Bool
allequal(f, itr) -> Bool
```

Retourne `true` si toutes les valeurs de `itr` sont égales lorsqu'elles sont comparées avec [`isequal`](@ref). Ou si toutes les valeurs de `[f(x) for x in itr]` sont égales, pour la deuxième méthode.

Notez que `allequal(f, itr)` peut appeler `f` moins de fois que `length(itr)`. Le nombre précis d'appels est considéré comme un détail d'implémentation.

Voir aussi : [`unique`](@ref), [`allunique`](@ref).

!!! compat "Julia 1.8"
    La fonction `allequal` nécessite au moins Julia 1.8.


!!! compat "Julia 1.11"
    La méthode `allequal(f, itr)` nécessite au moins Julia 1.11.


# Exemples

```jldoctest
julia> allequal([])
true

julia> allequal([1])
true

julia> allequal([1, 1])
true

julia> allequal([1, 2])
false

julia> allequal(Dict(:a => 1, :b => 1))
false

julia> allequal(abs2, [1, -1])
true
```
