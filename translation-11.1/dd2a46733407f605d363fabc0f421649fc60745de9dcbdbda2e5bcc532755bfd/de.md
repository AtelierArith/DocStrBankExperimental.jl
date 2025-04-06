```
isassigned(val::ScopedValue)
```

Überprüfen, ob ein `ScopedValue` einen zugewiesenen Wert hat.

Siehe auch: [`ScopedValues.with`](@ref), [`ScopedValues.@with`](@ref), [`ScopedValues.get`](@ref).

# Beispiele

```jldoctest
julia> using Base.ScopedValues

julia> a = ScopedValue(1); b = ScopedValue{Int}();

julia> isassigned(a)
true

julia> isassigned(b)
false
```
