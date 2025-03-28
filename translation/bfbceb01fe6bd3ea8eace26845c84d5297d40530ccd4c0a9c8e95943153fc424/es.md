```
get(val::ScopedValue{T})::Union{Nothing, Some{T}}
```

Si el valor de ámbito no está establecido y no tiene un valor predeterminado, devuelve `nothing`. De lo contrario, devuelve `Some{T}` con el valor actual.

Véase también: [`ScopedValues.with`](@ref), [`ScopedValues.@with`](@ref), [`ScopedValues.ScopedValue`](@ref).

# Ejemplos

```jldoctest
julia> using Base.ScopedValues

julia> a = ScopedValue(42); b = ScopedValue{Int}();

julia> ScopedValues.get(a)
Some(42)

julia> isnothing(ScopedValues.get(b))
true
```
