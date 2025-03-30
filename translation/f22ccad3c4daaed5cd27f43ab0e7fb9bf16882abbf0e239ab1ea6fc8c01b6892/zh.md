```
eigvecs(A; permute::Bool=true, scale::Bool=true, `sortby`) -> Matrix
```

返回一个矩阵 `M`，其列是 `A` 的特征向量。(`k`th 特征向量可以通过切片 `M[:, k]` 获得。) `permute`、`scale` 和 `sortby` 关键字与 [`eigen`](@ref) 相同。

# 示例

```jldoctest
julia> eigvecs([1.0 0.0 0.0; 0.0 3.0 0.0; 0.0 0.0 18.0])
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0
```
