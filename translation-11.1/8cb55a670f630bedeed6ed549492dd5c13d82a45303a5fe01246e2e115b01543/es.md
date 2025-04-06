```
count_ones(x::Integer) -> Integer
```

Número de unos en la representación binaria de `x`.

# Ejemplos

```jldoctest
julia> count_ones(7)
3

julia> count_ones(Int32(-1))
32
```
