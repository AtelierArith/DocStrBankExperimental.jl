```
rem(x, y, r::RoundingMode=RoundToZero)
```

Calcula el residuo de `x` después de la división entera por `y`, con el cociente redondeado de acuerdo con el modo de redondeo `r`. En otras palabras, la cantidad

```
x - y * round(x / y, r)
```

sin ningún redondeo intermedio.

  * si `r == RoundNearest`, entonces el resultado es exacto, y está en el intervalo $[-|y| / 2, |y| / 2]$. Ver también [`RoundNearest`](@ref).
  * si `r == RoundToZero` (por defecto), entonces el resultado es exacto, y está en el intervalo $[0, |y|)$ si `x` es positivo, o $(-|y|, 0]$ de lo contrario. Ver también [`RoundToZero`](@ref).
  * si `r == RoundDown`, entonces el resultado está en el intervalo $[0, y)$ si `y` es positivo, o $(y, 0]$ de lo contrario. El resultado puede no ser exacto si `x` y `y` tienen signos diferentes, y `abs(x) < abs(y)`. Ver también [`RoundDown`](@ref).
  * si `r == RoundUp`, entonces el resultado está en el intervalo $(-y, 0]$ si `y` es positivo, o $[0, -y)$ de lo contrario. El resultado puede no ser exacto si `x` y `y` tienen el mismo signo, y `abs(x) < abs(y)`. Ver también [`RoundUp`](@ref).
  * si `r == RoundFromZero`, entonces el resultado está en el intervalo $(-y, 0]$ si `y` es positivo, o $[0, -y)$ de lo contrario. El resultado puede no ser exacto si `x` y `y` tienen el mismo signo, y `abs(x) < abs(y)`. Ver también [`RoundFromZero`](@ref).

!!! compat "Julia 1.9"
    `RoundFromZero` requiere al menos Julia 1.9.


# Ejemplos:

```jldoctest
julia> x = 9; y = 4;

julia> x % y  # igual a rem(x, y)
1

julia> x ÷ y  # igual a div(x, y)
2

julia> x == div(x, y) * y + rem(x, y)
true
```
