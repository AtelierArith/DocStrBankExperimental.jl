```
GeneralizedSVD <: Factorization
```

广义奇异值分解（SVD）两矩阵 `A` 和 `B` 的矩阵分解类型，使得 `A = F.U*F.D1*F.R0*F.Q'` 和 `B = F.V*F.D2*F.R0*F.Q'`。这是 [`svd(_, _)`](@ref) 的返回类型，对应的矩阵分解函数。

对于一个 M 行 N 列的矩阵 `A` 和一个 P 行 N 列的矩阵 `B`，

  * `U` 是一个 M 行 M 列的正交矩阵，
  * `V` 是一个 P 行 P 列的正交矩阵，
  * `Q` 是一个 N 行 N 列的正交矩阵，
  * `D1` 是一个 M 行 (K+L) 列的对角矩阵，前 K 个条目为 1，
  * `D2` 是一个 P 行 (K+L) 列的矩阵，其右上角的 L 行 L 列块为对角矩阵，
  * `R0` 是一个 (K+L) 行 N 列的矩阵，其最右侧的 (K+L) 行 (K+L) 列块是非奇异的上三角块，

`K+L` 是矩阵 `[A; B]` 的有效数值秩。

迭代分解产生组件 `U`、`V`、`Q`、`D1`、`D2` 和 `R0`。

`F.D1` 和 `F.D2` 的条目是相关的，具体说明见 LAPACK 文档中的 [广义 SVD](https://www.netlib.org/lapack/lug/node36.html) 和底层调用的 [xGGSVD3](https://www.netlib.org/lapack/explore-html/d6/db3/dggsvd3_8f.html) 例程（在 LAPACK 3.6.0 及更新版本中）。

# 示例

```jldoctest
julia> A = [1. 0.; 0. -1.]
2×2 Matrix{Float64}:
 1.0   0.0
 0.0  -1.0

julia> B = [0. 1.; 1. 0.]
2×2 Matrix{Float64}:
 0.0  1.0
 1.0  0.0

julia> F = svd(A, B)
GeneralizedSVD{Float64, Matrix{Float64}, Float64, Vector{Float64}}
U factor:
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
V factor:
2×2 Matrix{Float64}:
 -0.0  -1.0
  1.0   0.0
Q factor:
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
D1 factor:
2×2 Matrix{Float64}:
 0.707107  0.0
 0.0       0.707107
D2 factor:
2×2 Matrix{Float64}:
 0.707107  0.0
 0.0       0.707107
R0 factor:
2×2 Matrix{Float64}:
 1.41421   0.0
 0.0      -1.41421

julia> F.U*F.D1*F.R0*F.Q'
2×2 Matrix{Float64}:
 1.0   0.0
 0.0  -1.0

julia> F.V*F.D2*F.R0*F.Q'
2×2 Matrix{Float64}:
 -0.0  1.0
  1.0  0.0
```
