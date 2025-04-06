```
count_ones(x::Integer) -> Integer
```

Nombre de uns dans la représentation binaire de `x`.

# Exemples

```jldoctest
julia> count_ones(7)
3

julia> count_ones(Int32(-1))
32
```
