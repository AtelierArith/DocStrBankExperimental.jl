```
coalesce(x...)
```

Argümanlar arasında [`missing`](@ref) ile eşit olmayan ilk değeri döndürür, eğer varsa. Aksi takdirde `missing` döner.

Ayrıca bkz. [`skipmissing`](@ref), [`something`](@ref), [`@coalesce`](@ref).

# Örnekler

```jldoctest
julia> coalesce(missing, 1)
1

julia> coalesce(1, missing)
1

julia> coalesce(nothing, 1)  # `nothing` döner

julia> coalesce(missing, missing)
missing
```
