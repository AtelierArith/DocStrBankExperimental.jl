```
angle(z)
```

Berechnet den Phasenwinkel in Bogenmaß einer komplexen Zahl `z`.

Gibt eine Zahl `-pi ≤ angle(z) ≤ pi` zurück und ist somit entlang der negativen reellen Achse diskontinuierlich.

Siehe auch: [`atan`](@ref), [`cis`](@ref), [`rad2deg`](@ref).

# Beispiele

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
