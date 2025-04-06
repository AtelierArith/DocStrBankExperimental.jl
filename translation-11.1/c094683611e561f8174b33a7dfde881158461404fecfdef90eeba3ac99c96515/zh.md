```
lq(A) -> S::LQ
```

计算 `A` 的 LQ 分解。分解的下三角成分可以通过 [`LQ`](@ref) 对象 `S` 的 `S.L` 获得，正交/单位成分可以通过 `S.Q` 获得，从而有 `A ≈ S.L*S.Q`。

迭代分解会产生成分 `S.L` 和 `S.Q`。

LQ 分解是 `transpose(A)` 的 QR 分解，它在计算欠定方程组的最小范数解 `lq(A) \ b` 时非常有用（`A` 的列数大于行数，但具有满行秩）。

# 示例

```jldoctest
julia> A = [5. 7.; -2. -4.]
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> S = lq(A)
LQ{Float64, Matrix{Float64}, Vector{Float64}}
L 因子:
2×2 Matrix{Float64}:
 -8.60233   0.0
  4.41741  -0.697486
Q 因子: 2×2 LinearAlgebra.LQPackedQ{Float64, Matrix{Float64}, Vector{Float64}}

julia> S.L * S.Q
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> l, q = S; # 通过迭代解构

julia> l == S.L &&  q == S.Q
true
```
