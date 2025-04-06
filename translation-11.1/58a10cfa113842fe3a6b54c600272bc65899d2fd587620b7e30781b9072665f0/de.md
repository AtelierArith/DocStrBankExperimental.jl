```
asin(x)
```

Berechne den inversen Sinus von `x`, wobei die Ausgabe in Bogenmaß erfolgt.

Siehe auch [`asind`](@ref) für die Ausgabe in Grad.

# Beispiele

```jldoctest
julia> asin.((0, 1/2, 1))
(0.0, 0.5235987755982989, 1.5707963267948966)

julia> asind.((0, 1/2, 1))
(0.0, 30.000000000000004, 90.0)
```
