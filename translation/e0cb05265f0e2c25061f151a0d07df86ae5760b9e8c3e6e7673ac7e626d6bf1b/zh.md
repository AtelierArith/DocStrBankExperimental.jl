```
cos(A::AbstractMatrix)
```

计算方阵 `A` 的矩阵余弦。

如果 `A` 是对称的或厄米的，则使用其特征分解 ([`eigen`](@ref)) 来计算余弦。否则，通过调用 [`exp`](@ref) 来确定余弦。

# 示例

```jldoctest
julia> cos(fill(1.0, (2,2)))
2×2 Matrix{Float64}:
  0.291927  -0.708073
 -0.708073   0.291927
```
