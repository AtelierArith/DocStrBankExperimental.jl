```
leading_ones(x::Integer) -> Integer
```

Anzahl der Einsen, die die binäre Darstellung von `x` anführen.

# Beispiele

```jldoctest
julia> leading_ones(UInt32(2 ^ 32 - 2))
31
```
