```
UniformScaling{T<:Number}
```

定义为标量乘以单位算子的通用大小均匀缩放算子，`λ*I`。尽管没有明确的 `size`，在许多情况下它的行为类似于矩阵，并且支持某些索引。另见 [`I`](@ref)。

!!! compat "Julia 1.6"
    从 Julia 1.6 开始，支持使用范围进行索引。


# 示例

```jldoctest
julia> J = UniformScaling(2.)
UniformScaling{Float64}
2.0*I

julia> A = [1. 2.; 3. 4.]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> J*A
2×2 Matrix{Float64}:
 2.0  4.0
 6.0  8.0

julia> J[1:2, 1:2]
2×2 Matrix{Float64}:
 2.0  0.0
 0.0  2.0
```
