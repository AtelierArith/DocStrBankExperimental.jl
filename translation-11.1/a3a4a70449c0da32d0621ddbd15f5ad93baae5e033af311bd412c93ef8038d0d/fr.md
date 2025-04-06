```
angle(z)
```

Calcule l'angle de phase en radians d'un nombre complexe `z`.

Renvoie un nombre `-pi ≤ angle(z) ≤ pi`, et est donc discontinu le long de l'axe réel négatif.

Voir aussi : [`atan`](@ref), [`cis`](@ref), [`rad2deg`](@ref).

# Exemples

```jldoctest
julia> rad2deg(angle(1 + im))
45.0

julia> rad2deg(angle(1 - im))
-45.0

julia> rad2deg(angle(-1 + 1e-20im))
180.0

julia> rad2deg(angle(-1 - 1e-20im))
-180.0
```
