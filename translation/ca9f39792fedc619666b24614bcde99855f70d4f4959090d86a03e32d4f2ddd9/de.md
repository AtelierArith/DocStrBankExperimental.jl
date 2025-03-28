```
divrem(x, y, r::RoundingMode=RoundToZero)
```

Der Quotient und der Rest aus der euklidischen Division. Entspricht `(div(x, y, r), rem(x, y, r))`. Entsprechend ist dieser Aufruf mit dem Standardwert von `r` gleichbedeutend mit `(x ÷ y, x % y)`.

Siehe auch: [`fldmod`](@ref), [`cld`](@ref).

# Beispiele

```jldoctest
julia> divrem(3, 7)
(0, 3)

julia> divrem(7, 3)
(2, 1)
```
