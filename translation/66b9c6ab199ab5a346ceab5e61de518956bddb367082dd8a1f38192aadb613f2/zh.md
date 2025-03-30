```
eigvals(A; permute::Bool=true, scale::Bool=true, sortby) -> values
```

返回 `A` 的特征值。

对于一般的非对称矩阵，可以在特征值计算之前指定如何平衡矩阵。`permute`、`scale` 和 `sortby` 关键字与 [`eigen`](@ref) 相同。

# 示例

```jldoctest
julia> diag_matrix = [1 0; 0 4]
2×2 Matrix{Int64}:
 1  0
 0  4

julia> eigvals(diag_matrix)
2-element Vector{Float64}:
 1.0
 4.0
```
