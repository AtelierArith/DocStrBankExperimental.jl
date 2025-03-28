```
count_ones(x::Integer) -> Integer
```

Anzahl der Einsen in der binären Darstellung von `x`.

# Beispiele

```jldoctest
julia> count_ones(7)
3

julia> count_ones(Int32(-1))
32
```
