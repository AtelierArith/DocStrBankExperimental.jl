```
valtype(T::Type{<:AbstractArray})
valtype(A::AbstractArray)
```

Gibt den Werttyp eines Arrays zurück. Dies ist identisch zu [`eltype`](@ref) und wird hauptsächlich zur Kompatibilität mit der Dictionary-Schnittstelle bereitgestellt.

# Beispiele

```jldoctest
julia> valtype(["one", "two", "three"])
String
```

!!! compat "Julia 1.2"
    Für Arrays erfordert diese Funktion mindestens Julia 1.2.

