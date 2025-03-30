```
cbrt(A::AbstractMatrix{<:Real})
```

计算实值矩阵 `A` 的实值立方根。如果 `T = cbrt(A)`，则我们有 `T*T*T ≈ A`，请参见下面给出的示例。

如果 `A` 是对称的，即类型为 `HermOrSym{<:Real}`，则使用 ([`eigen`](@ref)) 来找到立方根。否则，利用专门的 p 次根算法 [^S03]，该算法利用实值 Schur 分解 ([`schur`](@ref)) 来计算立方根。

[^S03]: Matthew I. Smith, "A Schur Algorithm for Computing Matrix pth Roots", SIAM Journal on Matrix Analysis and Applications, vol. 24, 2003, pp. 971–989. [doi:10.1137/S0895479801392697](https://doi.org/10.1137/s0895479801392697)

# 示例

```jldoctest
julia> A = [0.927524 -0.15857; -1.3677 -1.01172]
2×2 Matrix{Float64}:
  0.927524  -0.15857
 -1.3677    -1.01172

julia> T = cbrt(A)
2×2 Matrix{Float64}:
  0.910077  -0.151019
 -1.30257   -0.936818

julia> T*T*T ≈ A
true
```
