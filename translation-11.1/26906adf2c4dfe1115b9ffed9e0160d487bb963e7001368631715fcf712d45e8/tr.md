```
AbstractRange{T} <: AbstractVector{T}
```

`T` türünden elemanlara sahip lineer aralıklar için süper tür. [`UnitRange`](@ref), [`LinRange`](@ref) ve diğer türler bunun alt türleridir.

Tüm alt türler [`step`](@ref) tanımlamalıdır. Bu nedenle [`LogRange`](@ref Base.LogRange) `AbstractRange`'in bir alt türü değildir.
