```
get(val::ScopedValue{T})::Union{Nothing, Some{T}}
```

Wenn der Scoped-Wert nicht gesetzt ist und keinen Standardwert hat, gibt er `nothing` zurück. Andernfalls gibt er `Some{T}` mit dem aktuellen Wert zurück.

Siehe auch: [`ScopedValues.with`](@ref), [`ScopedValues.@with`](@ref), [`ScopedValues.ScopedValue`](@ref).

# Beispiele

```jldoctest
julia> using Base.ScopedValues

julia> a = ScopedValue(42); b = ScopedValue{Int}();

julia> ScopedValues.get(a)
Some(42)

julia> isnothing(ScopedValues.get(b))
true
```
