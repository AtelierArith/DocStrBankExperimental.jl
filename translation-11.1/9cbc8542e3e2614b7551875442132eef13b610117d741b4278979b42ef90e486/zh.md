```
sin(A::AbstractMatrix)
```

计算方阵 `A` 的矩阵正弦。

如果 `A` 是对称的或厄米的，则使用其特征分解 ([`eigen`](@ref)) 来计算正弦。否则，通过调用 [`exp`](@ref) 来确定正弦。

# 示例

```jldoctest
julia> sin(fill(1.0, (2,2)))
2×2 Matrix{Float64}:
 0.454649  0.454649
 0.454649  0.454649
```
