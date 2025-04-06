```
tan(A::AbstractMatrix)
```

计算方阵 `A` 的矩阵切线。

如果 `A` 是对称的或厄米的，则使用其特征分解 ([`eigen`](@ref)) 来计算切线。否则，通过调用 [`exp`](@ref) 来确定切线。

# 示例

```jldoctest
julia> tan(fill(1.0, (2,2)))
2×2 Matrix{Float64}:
 -1.09252  -1.09252
 -1.09252  -1.09252
```
