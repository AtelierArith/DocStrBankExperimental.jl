```
nonmissingtype(T::Type)
```

Si `T` es una unión de tipos que contiene `Missing`, devuelve un nuevo tipo con `Missing` eliminado.

# Ejemplos

```jldoctest
julia> nonmissingtype(Union{Int64,Missing})
Int64

julia> nonmissingtype(Any)
Any
```

!!! compat "Julia 1.3"
    Esta función se exporta a partir de Julia 1.3.

