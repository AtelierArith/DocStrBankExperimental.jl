```
bunchkaufman(A, rook::Bool=false; check = true) -> S::BunchKaufman
```

计算对称或厄米矩阵 `A` 的 Bunch-Kaufman [^Bunch1977] 分解为 `P'*U*D*U'*P` 或 `P'*L*D*L'*P`，具体取决于 `A` 中存储的是哪个三角形，并返回一个 [`BunchKaufman`](@ref) 对象。请注意，如果 `A` 是复对称的，则 `U'` 和 `L'` 表示未共轭的转置，即 `transpose(U)` 和 `transpose(L)`。

迭代分解会产生组件 `S.D`、`S.U` 或 `S.L`，具体取决于 `S.uplo` 和 `S.p`。

如果 `rook` 为 `true`，则使用 rook 选主元。如果 `rook` 为 false，则不使用 rook 选主元。

当 `check = true` 时，如果分解失败，将抛出错误。当 `check = false` 时，检查分解有效性的责任（通过 [`issuccess`](@ref)）由用户承担。

以下函数可用于 `BunchKaufman` 对象：[`size`](@ref)、`\`、[`inv`](@ref)、[`issymmetric`](@ref)、[`ishermitian`](@ref)、[`getindex`](@ref)。

[^Bunch1977]: J R Bunch 和 L Kaufman, 一些稳定的方法用于计算惯性和求解对称线性系统, Mathematics of Computation 31:137 (1977), 163-179. [url](https://www.ams.org/journals/mcom/1977-31-137/S0025-5718-1977-0428694-0/).

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

julia> S.U*S.D*S.U' - S.P*A*S.P'
2×2 Matrix{Float64}:
 0.0  0.0
 0.0  0.0

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

julia> S.L*S.D*S.L' - A[S.p, S.p]
2×2 Matrix{Float64}:
 0.0  0.0
 0.0  0.0
```
