```
isassigned(val::ScopedValue)
```

Prueba si un `ScopedValue` tiene un valor asignado.

Ver también: [`ScopedValues.with`](@ref), [`ScopedValues.@with`](@ref), [`ScopedValues.get`](@ref).

# Ejemplos

```jldoctest
julia> using Base.ScopedValues

julia> a = ScopedValue(1); b = ScopedValue{Int}();

julia> isassigned(a)
true

julia> isassigned(b)
false
```
