```
rem2pi(x, r::RoundingMode)
```

Calcula el residuo de `x` después de la división entera por `2π`, con el cociente redondeado de acuerdo con el modo de redondeo `r`. En otras palabras, la cantidad

```
x - 2π*round(x/(2π),r)
```

sin ningún redondeo intermedio. Esto utiliza internamente una aproximación de alta precisión de 2π, y por lo tanto dará un resultado más preciso que `rem(x,2π,r)`

  * si `r == RoundNearest`, entonces el resultado está en el intervalo $[-π, π]$. Este será generalmente el resultado más preciso. Ver también [`RoundNearest`](@ref).
  * si `r == RoundToZero`, entonces el resultado está en el intervalo $[0, 2π]$ si `x` es positivo, o $[-2π, 0]$ de lo contrario. Ver también [`RoundToZero`](@ref).
  * si `r == RoundDown`, entonces el resultado está en el intervalo $[0, 2π]$. Ver también [`RoundDown`](@ref).
  * si `r == RoundUp`, entonces el resultado está en el intervalo $[-2π, 0]$. Ver también [`RoundUp`](@ref).

# Ejemplos

```jldoctest
julia> rem2pi(7pi/4, RoundNearest)
-0.7853981633974485

julia> rem2pi(7pi/4, RoundDown)
5.497787143782138
```
