```
get(val::ScopedValue{T})::Union{Nothing, Some{T}}
```

Si la valeur scoping n'est pas définie et n'a pas de valeur par défaut, retourne `nothing`. Sinon, retourne `Some{T}` avec la valeur actuelle.

Voir aussi : [`ScopedValues.with`](@ref), [`ScopedValues.@with`](@ref), [`ScopedValues.ScopedValue`](@ref).

# Exemples

```jldoctest
julia> using Base.ScopedValues

julia> a = ScopedValue(42); b = ScopedValue{Int}();

julia> ScopedValues.get(a)
Some(42)

julia> isnothing(ScopedValues.get(b))
true
```
