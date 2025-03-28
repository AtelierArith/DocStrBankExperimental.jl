```
valtype(T::Type{<:AbstractArray})
valtype(A::AbstractArray)
```

Devuelve el tipo de valor de un arreglo. Esto es idéntico a [`eltype`](@ref) y se proporciona principalmente por compatibilidad con la interfaz de diccionario.

# Ejemplos

```jldoctest
julia> valtype(["one", "two", "three"])
String
```

!!! compat "Julia 1.2"
    Para arreglos, esta función requiere al menos Julia 1.2.

