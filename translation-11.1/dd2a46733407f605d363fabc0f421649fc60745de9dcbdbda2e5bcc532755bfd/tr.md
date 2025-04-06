```
isassigned(val::ScopedValue)
```

Bir `ScopedValue`'ın atanmış bir değere sahip olup olmadığını test eder.

Ayrıca bakınız: [`ScopedValues.with`](@ref), [`ScopedValues.@with`](@ref), [`ScopedValues.get`](@ref).

# Örnekler

```jldoctest
julia> using Base.ScopedValues

julia> a = ScopedValue(1); b = ScopedValue{Int}();

julia> isassigned(a)
true

julia> isassigned(b)
false
```
