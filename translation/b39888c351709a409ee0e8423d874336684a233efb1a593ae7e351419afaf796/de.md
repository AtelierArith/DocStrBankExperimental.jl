```
rem(x, y, r::RoundingMode=RoundToZero)
```

Berechne den Rest von `x` nach der ganzzahligen Division durch `y`, wobei der Quotient gemäß dem Rundungsmodus `r` gerundet wird. Mit anderen Worten, die Größe

```
x - y * round(x / y, r)
```

ohne Zwischenrundung.

  * wenn `r == RoundNearest`, dann ist das Ergebnis genau und im Intervall $[-|y| / 2, |y| / 2]$. Siehe auch [`RoundNearest`](@ref).
  * wenn `r == RoundToZero` (Standard), dann ist das Ergebnis genau und im Intervall $[0, |y|)$, wenn `x` positiv ist, oder $(-|y|, 0]$ andernfalls. Siehe auch [`RoundToZero`](@ref).
  * wenn `r == RoundDown`, dann liegt das Ergebnis im Intervall $[0, y)$, wenn `y` positiv ist, oder $(y, 0]$ andernfalls. Das Ergebnis kann ungenau sein, wenn `x` und `y` unterschiedliche Vorzeichen haben und `abs(x) < abs(y)`. Siehe auch [`RoundDown`](@ref).
  * wenn `r == RoundUp`, dann liegt das Ergebnis im Intervall $(-y, 0]$, wenn `y` positiv ist, oder $[0, -y)$ andernfalls. Das Ergebnis kann ungenau sein, wenn `x` und `y` dasselbe Vorzeichen haben und `abs(x) < abs(y)`. Siehe auch [`RoundUp`](@ref).
  * wenn `r == RoundFromZero`, dann liegt das Ergebnis im Intervall $(-y, 0]$, wenn `y` positiv ist, oder $[0, -y)$ andernfalls. Das Ergebnis kann ungenau sein, wenn `x` und `y` dasselbe Vorzeichen haben und `abs(x) < abs(y)`. Siehe auch [`RoundFromZero`](@ref).

!!! compat "Julia 1.9"
    `RoundFromZero` erfordert mindestens Julia 1.9.


# Beispiele:

```jldoctest
julia> x = 9; y = 4;

julia> x % y  # dasselbe wie rem(x, y)
1

julia> x ÷ y  # dasselbe wie div(x, y)
2

julia> x == div(x, y) * y + rem(x, y)
true
```
