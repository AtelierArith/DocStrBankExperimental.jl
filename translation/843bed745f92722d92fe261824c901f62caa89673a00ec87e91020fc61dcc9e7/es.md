```
valtype(type)
```

Obtiene el tipo de valor de un tipo de diccionario. Se comporta de manera similar a [`eltype`](@ref).

# Ejemplos

```jldoctest
julia> valtype(Dict(Int32(1) => "foo"))
String
```
