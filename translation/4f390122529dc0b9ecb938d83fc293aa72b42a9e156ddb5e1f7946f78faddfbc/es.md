```
div(x, y, r::RoundingMode=RoundToZero)
```

El cociente de la división euclidiana (entera). Calcula `x / y`, redondeado a un entero de acuerdo con el modo de redondeo `r`. En otras palabras, la cantidad

```
round(x / y, r)
```

sin ningún redondeo intermedio.

!!! compat "Julia 1.4"
    El método de tres argumentos que toma un `RoundingMode` requiere Julia 1.4 o posterior.


Véase también [`fld`](@ref) y [`cld`](@ref), que son casos especiales de esta función.

!!! compat "Julia 1.9"
    `RoundFromZero` requiere al menos Julia 1.9.


# Ejemplos:

```jldoctest
julia> div(4, 3, RoundToZero) # Coincide con div(4, 3)
1
julia> div(4, 3, RoundDown) # Coincide con fld(4, 3)
1
julia> div(4, 3, RoundUp) # Coincide con cld(4, 3)
2
julia> div(5, 2, RoundNearest)
2
julia> div(5, 2, RoundNearestTiesAway)
3
julia> div(-5, 2, RoundNearest)
-2
julia> div(-5, 2, RoundNearestTiesAway)
-3
julia> div(-5, 2, RoundNearestTiesUp)
-2
julia> div(4, 3, RoundFromZero)
2
julia> div(-4, 3, RoundFromZero)
-2
```
