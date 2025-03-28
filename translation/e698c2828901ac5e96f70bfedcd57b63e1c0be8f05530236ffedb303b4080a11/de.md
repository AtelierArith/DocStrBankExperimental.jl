```
promote_typejoin(T, S)
```

Berechne einen Typ, der sowohl `T` als auch `S` enthält, der entweder ein Elternteil beider Typen sein könnte oder ein `Union`, wenn es angemessen ist. Fällt zurück auf [`typejoin`](@ref).

Siehe auch [`promote`](@ref), [`promote_type`](@ref).

# Beispiele

```jldoctest
julia> Base.promote_typejoin(Int, Float64)
Real

julia> Base.promote_type(Int, Float64)
Float64
```
