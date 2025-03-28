```
leading_ones(x::Integer) -> Integer
```

Número de unos que preceden la representación binaria de `x`.

# Ejemplos

```jldoctest
julia> leading_ones(UInt32(2 ^ 32 - 2))
31
```
