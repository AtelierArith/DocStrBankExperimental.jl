```
rem2pi(x, r::RoundingMode)
```

Berechnet den Rest von `x` nach der ganzzahligen Division durch `2π`, wobei der Quotient gemäß dem Rundungsmodus `r` gerundet wird. Mit anderen Worten, die Größe

```
x - 2π*round(x/(2π),r)
```

ohne Zwischenrundung. Dies verwendet intern eine hochpräzise Näherung von 2π und liefert daher ein genaueres Ergebnis als `rem(x,2π,r)`

  * wenn `r == RoundNearest`, dann liegt das Ergebnis im Intervall $[-π, π]$. Dies wird im Allgemeinen das genaueste Ergebnis sein. Siehe auch [`RoundNearest`](@ref).
  * wenn `r == RoundToZero`, dann liegt das Ergebnis im Intervall $[0, 2π]$, wenn `x` positiv ist, oder $[-2π, 0]$ andernfalls. Siehe auch [`RoundToZero`](@ref).
  * wenn `r == RoundDown`, dann liegt das Ergebnis im Intervall $[0, 2π]$. Siehe auch [`RoundDown`](@ref).
  * wenn `r == RoundUp`, dann liegt das Ergebnis im Intervall $[-2π, 0]$. Siehe auch [`RoundUp`](@ref).

# Beispiele

```jldoctest
julia> rem2pi(7pi/4, RoundNearest)
-0.7853981633974485

julia> rem2pi(7pi/4, RoundDown)
5.497787143782138
```
