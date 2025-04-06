```
round(z::Complex[, RoundingModeReal, [RoundingModeImaginary]])
round(z::Complex[, RoundingModeReal, [RoundingModeImaginary]]; digits=0, base=10)
round(z::Complex[, RoundingModeReal, [RoundingModeImaginary]]; sigdigits, base=10)
```

Devuelve el valor integral más cercano del mismo tipo que el valor complejo `z`, rompiendo empates utilizando los [`RoundingMode`](@ref) especificados. El primer [`RoundingMode`](@ref) se utiliza para redondear los componentes reales, mientras que el segundo se utiliza para redondear los componentes imaginarios.

`RoundingModeReal` y `RoundingModeImaginary` se establecen de forma predeterminada en [`RoundNearest`](@ref), que redondea al entero más cercano, con empates (valores fraccionarios de 0.5) redondeados al entero par más cercano.

# Ejemplos

```jldoctest
julia> round(3.14 + 4.5im)
3.0 + 4.0im

julia> round(3.14 + 4.5im, RoundUp, RoundNearestTiesUp)
4.0 + 5.0im

julia> round(3.14159 + 4.512im; digits = 1)
3.1 + 4.5im

julia> round(3.14159 + 4.512im; sigdigits = 3)
3.14 + 4.51im
```
