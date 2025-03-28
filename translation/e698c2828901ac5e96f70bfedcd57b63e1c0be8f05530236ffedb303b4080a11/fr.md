```
promote_typejoin(T, S)
```

Calcule un type qui contient à la fois `T` et `S`, qui pourrait être soit un parent des deux types, soit un `Union` si approprié. Fait appel à [`typejoin`](@ref) en cas de besoin.

Voir aussi [`promote`](@ref), [`promote_type`](@ref).

# Exemples

```jldoctest
julia> Base.promote_typejoin(Int, Float64)
Real

julia> Base.promote_type(Int, Float64)
Float64
```
