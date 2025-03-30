```
SVD <: Factorization
```

矩阵 `A` 的奇异值分解（SVD）的矩阵分解类型。这是 [`svd(_)`](@ref) 的返回类型，对应的矩阵分解函数。

如果 `F::SVD` 是分解对象，则可以通过 `F.U`、`F.S`、`F.V` 和 `F.Vt` 获取 `U`、`S`、`V` 和 `Vt`，使得 `A = U * Diagonal(S) * Vt`。`S` 中的奇异值按降序排列。

迭代分解会产生组件 `U`、`S` 和 `V`。

# 示例

```jldoctest
julia> A = [1. 0. 0. 0. 2.; 0. 0. 3. 0. 0.; 0. 0. 0. 0. 0.; 0. 2. 0. 0. 0.]
4×5 Matrix{Float64}:
 1.0  0.0  0.0  0.0  2.0
 0.0  0.0  3.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  2.0  0.0  0.0  0.0

julia> F = svd(A)
SVD{Float64, Float64, Matrix{Float64}, Vector{Float64}}
U factor:
4×4 Matrix{Float64}:
 0.0  1.0   0.0  0.0
 1.0  0.0   0.0  0.0
 0.0  0.0   0.0  1.0
 0.0  0.0  -1.0  0.0
singular values:
4-element Vector{Float64}:
 3.0
 2.23606797749979
 2.0
 0.0
Vt factor:
4×5 Matrix{Float64}:
 -0.0        0.0  1.0  -0.0  0.0
  0.447214   0.0  0.0   0.0  0.894427
  0.0       -1.0  0.0   0.0  0.0
  0.0        0.0  0.0   1.0  0.0

julia> F.U * Diagonal(F.S) * F.Vt
4×5 Matrix{Float64}:
 1.0  0.0  0.0  0.0  2.0
 0.0  0.0  3.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  2.0  0.0  0.0  0.0

julia> u, s, v = F; # 通过迭代解构

julia> u == F.U && s == F.S && v == F.V
true
```
