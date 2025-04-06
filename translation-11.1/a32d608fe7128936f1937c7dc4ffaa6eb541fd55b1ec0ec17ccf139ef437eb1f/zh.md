```
Schur <: Factorization
```

矩阵 `A` 的 Schur 分解的矩阵分解类型。这是 [`schur(_)`](@ref) 的返回类型，对应的矩阵分解函数。

如果 `F::Schur` 是分解对象，则 (准) 三角形 Schur 因子可以通过 `F.Schur` 或 `F.T` 获得，正交/单位 Schur 向量可以通过 `F.vectors` 或 `F.Z` 获得，使得 `A = F.vectors * F.Schur * F.vectors'`。矩阵 `A` 的特征值可以通过 `F.values` 获得。

迭代分解会产生组件 `F.T`、`F.Z` 和 `F.values`。

# 示例

```jldoctest
julia> A = [5. 7.; -2. -4.]
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> F = schur(A)
Schur{Float64, Matrix{Float64}, Vector{Float64}}
T factor:
2×2 Matrix{Float64}:
 3.0   9.0
 0.0  -2.0
Z factor:
2×2 Matrix{Float64}:
  0.961524  0.274721
 -0.274721  0.961524
eigenvalues:
2-element Vector{Float64}:
  3.0
 -2.0

julia> F.vectors * F.Schur * F.vectors'
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> t, z, vals = F; # destructuring via iteration

julia> t == F.T && z == F.Z && vals == F.values
true
```
