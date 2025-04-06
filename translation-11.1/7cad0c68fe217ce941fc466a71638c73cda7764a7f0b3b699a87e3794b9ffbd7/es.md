```
keytype(type)
```

Obtiene el tipo de clave de un tipo de diccionario. Se comporta de manera similar a [`eltype`](@ref).

# Ejemplos

```jldoctest
julia> keytype(Dict(Int32(1) => "foo"))
Int32
```
