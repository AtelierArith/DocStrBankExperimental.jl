```
count_zeros(x::Integer) -> Integer
```

Anzahl der Nullen in der binären Darstellung von `x`.

# Beispiele

```jldoctest
julia> count_zeros(Int32(2 ^ 16 - 1))
16

julia> count_zeros(-1)
0
```
