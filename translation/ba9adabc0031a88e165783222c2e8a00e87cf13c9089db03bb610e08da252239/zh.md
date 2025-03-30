```
Eigen <: Factorization
```

矩阵分解类型，表示方阵 `A` 的特征值/谱分解。这是 [`eigen`](@ref) 的返回类型，对应的矩阵分解函数。

如果 `F::Eigen` 是分解对象，可以通过 `F.values` 获取特征值，通过矩阵 `F.vectors` 的列获取特征向量。（第 `k` 个特征向量可以通过切片 `F.vectors[:, k]` 获取。）

迭代分解会产生组件 `F.values` 和 `F.vectors`。

# 示例

```jldoctest
julia> F = eigen([1.0 0.0 0.0; 0.0 3.0 0.0; 0.0 0.0 18.0])
Eigen{Float64, Float64, Matrix{Float64}, Vector{Float64}}
values:
3-element Vector{Float64}:
  1.0
  3.0
 18.0
vectors:
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> F.values
3-element Vector{Float64}:
  1.0
  3.0
 18.0

julia> F.vectors
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> vals, vecs = F; # 通过迭代解构

julia> vals == F.values && vecs == F.vectors
true
```
