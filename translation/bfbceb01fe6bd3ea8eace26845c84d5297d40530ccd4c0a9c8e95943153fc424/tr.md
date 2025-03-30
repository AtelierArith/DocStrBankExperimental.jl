```
get(val::ScopedValue{T})::Union{Nothing, Some{T}}
```

Eğer kapsamlı değer ayarlanmamışsa ve varsayılan bir değeri yoksa, `nothing` döndür. Aksi takdirde, mevcut değeri ile `Some{T}` döndürür.

Ayrıca bakınız: [`ScopedValues.with`](@ref), [`ScopedValues.@with`](@ref), [`ScopedValues.ScopedValue`](@ref).

# Örnekler

```jldoctest
julia> using Base.ScopedValues

julia> a = ScopedValue(42); b = ScopedValue{Int}();

julia> ScopedValues.get(a)
Some(42)

julia> isnothing(ScopedValues.get(b))
true
```
