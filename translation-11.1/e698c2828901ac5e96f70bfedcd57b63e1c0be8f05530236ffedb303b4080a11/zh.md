```
promote_typejoin(T, S)
```

计算一个包含 `T` 和 `S` 的类型，这可能是两个类型的父类型，或者在适当的情况下是一个 `Union`。回退到 [`typejoin`](@ref)。

另见 [`promote`](@ref), [`promote_type`](@ref)。

# 示例

```jldoctest
julia> Base.promote_typejoin(Int, Float64)
Real

julia> Base.promote_type(Int, Float64)
Float64
```
