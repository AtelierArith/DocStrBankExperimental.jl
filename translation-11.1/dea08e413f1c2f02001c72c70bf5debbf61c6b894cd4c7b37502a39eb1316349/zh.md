```
伴随
```

用于底层线性代数对象的伴随视图的惰性包装类型，通常是 `AbstractVector`/`AbstractMatrix`。通常，不应直接调用 `Adjoint` 构造函数，而应使用 [`adjoint`](@ref)。要实现视图，请使用 [`copy`](@ref)。

此类型旨在用于线性代数 - 有关一般数据操作，请参见 [`permutedims`](@ref Base.permutedims)。

# 示例

```jldoctest
julia> A = [3+2im 9+2im; 0 0]
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 0+0im  0+0im

julia> Adjoint(A)
2×2 adjoint(::Matrix{Complex{Int64}}) with eltype Complex{Int64}:
 3-2im  0+0im
 9-2im  0+0im
```
