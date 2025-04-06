```
promote_type(type1, type2, ...)
```

提升指的是将混合类型的值转换为单一的公共类型。`promote_type` 表示 Julia 中默认的提升行为，当运算符（通常是数学运算）接收到不同类型的参数时。`promote_type` 通常尝试返回一种类型，该类型至少可以近似表示任一输入类型的大多数值，而不会过度扩展。某些损失是可以容忍的；例如，`promote_type(Int64, Float64)` 返回 [`Float64`](@ref)，即使严格来说，并非所有 [`Int64`](@ref) 值都可以精确表示为 `Float64` 值。

另请参见：[`promote`](@ref)，[`promote_typejoin`](@ref)，[`promote_rule`](@ref)。

# 示例

```jldoctest
julia> promote_type(Int64, Float64)
Float64

julia> promote_type(Int32, Int64)
Int64

julia> promote_type(Float32, BigInt)
BigFloat

julia> promote_type(Int16, Float16)
Float16

julia> promote_type(Int64, Float16)
Float16

julia> promote_type(Int8, UInt16)
UInt16
```

!!! warning "不要直接重载此函数"
    要为您自己的类型重载提升，您应该重载 [`promote_rule`](@ref)。`promote_type` 在内部调用 `promote_rule` 来确定类型。直接重载 `promote_type` 可能会导致歧义错误。

