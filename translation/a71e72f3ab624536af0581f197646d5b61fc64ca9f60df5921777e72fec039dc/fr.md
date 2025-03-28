```
count_zeros(x::Integer) -> Integer
```

Nombre de zéros dans la représentation binaire de `x`.

# Exemples

```jldoctest
julia> count_zeros(Int32(2 ^ 16 - 1))
16

julia> count_zeros(-1)
0
```
