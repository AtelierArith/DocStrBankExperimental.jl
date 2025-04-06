```
fieldname(x::DataType, i::Integer)
```

Bir `DataType`'in `i` numaralı alanının adını alır.

# Örnekler

```jldoctest
julia> fieldname(Rational, 1)
:num

julia> fieldname(Rational, 2)
:den
```
