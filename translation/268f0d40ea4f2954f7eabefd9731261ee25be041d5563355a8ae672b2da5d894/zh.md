```
转置
```

用于底层线性代数对象的转置视图的惰性包装类型，通常是 `AbstractVector`/`AbstractMatrix`。通常不应直接调用 `Transpose` 构造函数，而应使用 [`transpose`](@ref) 代替。要实现视图，请使用 [`copy`](@ref)。

此类型旨在用于线性代数使用 - 有关一般数据操作，请参见 [`permutedims`](@ref Base.permutedims)。

# 示例

```jldoctest
julia> A = [2 3; 0 0]
2×2 Matrix{Int64}:
 2  3
 0  0

julia> Transpose(A)
2×2 transpose(::Matrix{Int64}) with eltype Int64:
 2  0
 3  0
```
