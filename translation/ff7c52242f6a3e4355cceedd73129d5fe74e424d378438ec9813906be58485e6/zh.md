```
LQ <: 因式分解
```

矩阵 `A` 的 `LQ` 因式分解类型。`LQ` 分解是 `transpose(A)` 的 [`QR`](@ref) 分解。这是 [`lq`](@ref) 的返回类型，对应的矩阵因式分解函数。

如果 `S::LQ` 是因式分解对象，则可以通过 `S.L` 获取下三角组件，通过 `S.Q` 获取正交/单位组件，使得 `A ≈ S.L*S.Q`。

迭代分解会产生组件 `S.L` 和 `S.Q`。

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
