```
schur(A) -> F::Schur
```

计算矩阵 `A` 的 Schur 分解。可以通过 `F.Schur` 或 `F.T` 从 `Schur` 对象 `F` 中获得（准）三角 Schur 因子，正交/单位 Schur 向量可以通过 `F.vectors` 或 `F.Z` 获得，从而满足 `A = F.vectors * F.Schur * F.vectors'`。可以通过 `F.values` 获得 `A` 的特征值。

对于实数矩阵 `A`，Schur 分解是“准三角形”的，这意味着它是上三角的，除了对于任何共轭复特征值的 2×2 对角块；这使得即使存在复特征值，分解也可以完全是实数的。要从实数准三角分解中获得（复数）纯上三角的 Schur 分解，可以使用 `Schur{Complex}(schur(A))`。

迭代分解会产生组件 `F.T`、`F.Z` 和 `F.values`。

# 示例

```jldoctest
julia> A = [5. 7.; -2. -4.]
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> F = schur(A)
Schur{Float64, Matrix{Float64}, Vector{Float64}}
T 因子:
2×2 Matrix{Float64}:
 3.0   9.0
 0.0  -2.0
Z 因子:
2×2 Matrix{Float64}:
  0.961524  0.274721
 -0.274721  0.961524
特征值:
2-element Vector{Float64}:
  3.0
 -2.0

julia> F.vectors * F.Schur * F.vectors'
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> t, z, vals = F; # 通过迭代解构

julia> t == F.T && z == F.Z && vals == F.values
true
```
