```
leading_ones(x::Integer) -> Integer
```

`x`'in ikili temsilindeki baştaki 1'lerin sayısı.

# Örnekler

```jldoctest
julia> leading_ones(UInt32(2 ^ 32 - 2))
31
```
