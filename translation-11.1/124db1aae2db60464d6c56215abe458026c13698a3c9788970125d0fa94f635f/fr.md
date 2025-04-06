```
fieldname(x::DataType, i::Integer)
```

Obtenez le nom du champ `i` d'un `DataType`.

# Exemples

```jldoctest
julia> fieldname(Rational, 1)
:num

julia> fieldname(Rational, 2)
:den
```
