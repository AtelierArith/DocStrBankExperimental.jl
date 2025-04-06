```
count_zeros(x::Integer) -> Integer
```

`x`'in ikili temsilindeki sıfır sayısı.

# Örnekler

```jldoctest
julia> count_zeros(Int32(2 ^ 16 - 1))
16

julia> count_zeros(-1)
0
```
