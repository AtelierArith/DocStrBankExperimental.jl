```
leading_ones(x::Integer) -> Integer
```

Nombre de uns menant la représentation binaire de `x`.

# Exemples

```jldoctest
julia> leading_ones(UInt32(2 ^ 32 - 2))
31
```
