```
isassigned(val::ScopedValue)
```

Testez si un `ScopedValue` a une valeur assignée.

Voir aussi : [`ScopedValues.with`](@ref), [`ScopedValues.@with`](@ref), [`ScopedValues.get`](@ref).

# Exemples

```jldoctest
julia> using Base.ScopedValues

julia> a = ScopedValue(1); b = ScopedValue{Int}();

julia> isassigned(a)
true

julia> isassigned(b)
false
```
