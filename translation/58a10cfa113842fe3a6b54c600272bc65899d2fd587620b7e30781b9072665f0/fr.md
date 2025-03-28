```
asin(x)
```

Calcule l'arc sinus de `x`, où la sortie est en radians.

Voir aussi [`asind`](@ref) pour une sortie en degrés.

# Exemples

```jldoctest
julia> asin.((0, 1/2, 1))
(0.0, 0.5235987755982989, 1.5707963267948966)

julia> asind.((0, 1/2, 1))
(0.0, 30.000000000000004, 90.0)
```
