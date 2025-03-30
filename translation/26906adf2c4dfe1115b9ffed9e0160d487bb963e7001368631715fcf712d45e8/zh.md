```
AbstractRange{T} <: AbstractVector{T}
```

线性范围的超类型，其元素类型为 `T`。 [`UnitRange`](@ref)、[`LinRange`](@ref) 和其他类型是其子类型。

所有子类型必须定义 [`step`](@ref)。因此 [`LogRange`](@ref Base.LogRange) 不是 `AbstractRange` 的子类型。
