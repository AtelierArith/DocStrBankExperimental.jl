```
divrem(x, y, r::RoundingMode=RoundToZero)
```

El cociente y el residuo de la división euclidiana. Equivalente a `(div(x, y, r), rem(x, y, r))`. Equivalentemente, con el valor predeterminado de `r`, esta llamada es equivalente a `(x ÷ y, x % y)`.

Véase también: [`fldmod`](@ref), [`cld`](@ref).

# Ejemplos

```jldoctest
julia> divrem(3, 7)
(0, 3)

julia> divrem(7, 3)
(2, 1)
```
