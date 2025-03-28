```
keytype(T::Type{<:AbstractArray})
keytype(A::AbstractArray)
```

Devuelve el tipo de clave de un arreglo. Esto es igual al [`eltype`](@ref) del resultado de `keys(...)`, y se proporciona principalmente por compatibilidad con la interfaz de diccionario.

# Ejemplos

```jldoctest
julia> keytype([1, 2, 3]) == Int
true

julia> keytype([1 2; 3 4])
CartesianIndex{2}
```

!!! compat "Julia 1.2"
    Para arreglos, esta función requiere al menos Julia 1.2.

