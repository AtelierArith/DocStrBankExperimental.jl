```
fieldname(x::DataType, i::Integer)
```

Obtiene el nombre del campo `i` de un `DataType`.

# Ejemplos

```jldoctest
julia> fieldname(Rational, 1)
:num

julia> fieldname(Rational, 2)
:den
```
