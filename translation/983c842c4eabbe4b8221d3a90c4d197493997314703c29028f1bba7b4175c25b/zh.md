```
BunchKaufman <: Factorization
```

矩阵分解类型的 Bunch-Kaufman 分解用于对称或厄米矩阵 `A`，表示为 `P'UDU'P` 或 `P'LDL'P`，具体取决于 `A` 中存储的是上三角（默认）还是下三角。如果 `A` 是复对称的，则 `U'` 和 `L'` 表示非共轭转置，即分别为 `transpose(U)` 和 `transpose(L)`。这是 [`bunchkaufman`](@ref) 的返回类型，对应的矩阵分解函数。

如果 `S::BunchKaufman` 是分解对象，则可以通过 `S.D`、`S.U` 或 `S.L` 获取组件，具体取决于 `S.uplo` 和 `S.p`。

迭代分解会生成组件 `S.D`、`S.U` 或 `S.L`，具体取决于 `S.uplo` 和 `S.p`。

# 示例

```jldoctest
julia> A = Float64.([1 2; 2 3])
2×2 Matrix{Float64}:
 1.0  2.0
 2.0  3.0

julia> S = bunchkaufman(A) # A 在内部被 Symmetric(A) 包装
BunchKaufman{Float64, Matrix{Float64}, Vector{Int64}}
D 因子:
2×2 Tridiagonal{Float64, Vector{Float64}}:
 -0.333333  0.0
  0.0       3.0
U 因子:
2×2 UnitUpperTriangular{Float64, Matrix{Float64}}:
 1.0  0.666667
  ⋅   1.0
置换:
2-element Vector{Int64}:
 1
 2

julia> d, u, p = S; # 通过迭代解构

julia> d == S.D && u == S.U && p == S.p
true

julia> S = bunchkaufman(Symmetric(A, :L))
BunchKaufman{Float64, Matrix{Float64}, Vector{Int64}}
D 因子:
2×2 Tridiagonal{Float64, Vector{Float64}}:
 3.0   0.0
 0.0  -0.333333
L 因子:
2×2 UnitLowerTriangular{Float64, Matrix{Float64}}:
 1.0        ⋅
 0.666667  1.0
置换:
2-element Vector{Int64}:
 2
 1
```
