```
keytype(T::Type{<:AbstractArray})
keytype(A::AbstractArray)
```

Gibt den Schlüsseltyp eines Arrays zurück. Dies entspricht dem [`eltype`](@ref) des Ergebnisses von `keys(...)` und wird hauptsächlich zur Kompatibilität mit der Dictionary-Schnittstelle bereitgestellt.

# Beispiele

```jldoctest
julia> keytype([1, 2, 3]) == Int
true

julia> keytype([1 2; 3 4])
CartesianIndex{2}
```

!!! compat "Julia 1.2"
    Für Arrays erfordert diese Funktion mindestens Julia 1.2.

