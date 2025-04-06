```
ones([T=Float64,] dims::Tuple)
ones([T=Float64,] dims...)
```

创建一个元素类型为 `T` 的 `Array`，其大小由 `dims` 指定，所有元素均为一。另见 [`fill`](@ref)，[`zeros`](@ref)。

# 示例

```jldoctest
julia> ones(1,2)
1×2 Matrix{Float64}:
 1.0  1.0

julia> ones(ComplexF64, 2, 3)
2×3 Matrix{ComplexF64}:
 1.0+0.0im  1.0+0.0im  1.0+0.0im
 1.0+0.0im  1.0+0.0im  1.0+0.0im
```
