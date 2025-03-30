```
log(A::AbstractMatrix)
```

如果 `A` 没有负实特征值，计算 `A` 的主矩阵对数，即唯一的矩阵 $X$ 使得 $e^X = A$ 且对于所有特征值 $\lambda$，满足 $-\pi < Im(\lambda) < \pi$。如果 `A` 有非正特征值，则在可能的情况下返回非主矩阵函数。

如果 `A` 是对称或厄米的，则使用其特征分解（[`eigen`](@ref)），如果 `A` 是三角形的，则采用改进的逆缩放和平方方法（见 [^AH12] 和 [^AHR13]）。如果 `A` 是实数且没有负特征值，则计算实施尔形式。否则，计算复施尔形式。然后在上三角（准）三角因子上使用 [^AHR13] 中的上（准）三角算法。

[^AH12]: Awad H. Al-Mohy 和 Nicholas J. Higham, "改进的逆缩放和平方算法用于矩阵对数", SIAM Journal on Scientific Computing, 34(4), 2012, C153-C169. [doi:10.1137/110852553](https://doi.org/10.1137/110852553)

[^AHR13]: Awad H. Al-Mohy, Nicholas J. Higham 和 Samuel D. Relton, "计算矩阵对数的 Fréchet 导数并估计条件数", SIAM Journal on Scientific Computing, 35(4), 2013, C394-C410. [doi:10.1137/120885991](https://doi.org/10.1137/120885991)

# 示例

```jldoctest
julia> A = Matrix(2.7182818*I, 2, 2)
2×2 Matrix{Float64}:
 2.71828  0.0
 0.0      2.71828

julia> log(A)
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
```
