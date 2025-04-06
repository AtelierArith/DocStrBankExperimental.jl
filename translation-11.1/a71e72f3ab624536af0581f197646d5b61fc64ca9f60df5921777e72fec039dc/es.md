```
count_zeros(x::Integer) -> Integer
```

Número de ceros en la representación binaria de `x`.

# Ejemplos

```jldoctest
julia> count_zeros(Int32(2 ^ 16 - 1))
16

julia> count_zeros(-1)
0
```
