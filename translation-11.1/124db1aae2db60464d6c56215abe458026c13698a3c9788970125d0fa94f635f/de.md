```
fieldname(x::DataType, i::Integer)
```

Erhalte den Namen des Feldes `i` eines `DataType`.

# Beispiele

```jldoctest
julia> fieldname(Rational, 1)
:num

julia> fieldname(Rational, 2)
:den
```
