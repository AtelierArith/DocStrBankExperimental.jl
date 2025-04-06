```
promote_typejoin(T, S)
```

`T` ve `S`'yi içeren bir tür hesaplayın; bu, her iki türün de bir üst türü veya uygun olduğunda bir `Union` olabilir. [`typejoin`](@ref) ile geri döner.

Bunun yerine [`promote`](@ref), [`promote_type`](@ref) bakın.

# Örnekler

```jldoctest
julia> Base.promote_typejoin(Int, Float64)
Real

julia> Base.promote_type(Int, Float64)
Float64
```
