```
angle(z)
```

Calcula el ángulo de fase en radianes de un número complejo `z`.

Devuelve un número `-pi ≤ angle(z) ≤ pi`, y es, por lo tanto, discontinuo a lo largo del eje real negativo.

Véase también: [`atan`](@ref), [`cis`](@ref), [`rad2deg`](@ref).

# Ejemplos

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
