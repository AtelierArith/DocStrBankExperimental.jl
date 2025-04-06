```
significand(x)
```

Extrahiert den Signifikanten (auch bekannt als Mantisse) einer Fließkommazahl. Wenn `x` eine von Null verschiedene endliche Zahl ist, dann wird das Ergebnis eine Zahl vom gleichen Typ und Vorzeichen wie `x` sein, deren absoluter Wert im Intervall $[1,2)$ liegt. Andernfalls wird `x` zurückgegeben.

Siehe auch [`frexp`](@ref), [`exponent`](@ref).

# Beispiele

```jldoctest
julia> significand(15.2)
1.9

julia> significand(-15.2)
-1.9

julia> significand(-15.2) * 2^3
-15.2

julia> significand(-Inf), significand(Inf), significand(NaN)
(-Inf, Inf, NaN)
```
