```
exp(A::AbstractMatrix)
```

计算矩阵 `A` 的指数，定义为

$$
e^A = \sum_{n=0}^{\infty} \frac{A^n}{n!}.
$$

对于对称或厄米 `A`，使用特征分解 ([`eigen`](@ref))，否则选择缩放和平方算法（参见 [^H05]）。

[^H05]: Nicholas J. Higham, "The squaring and scaling method for the matrix exponential revisited", SIAM Journal on Matrix Analysis and Applications, 26(4), 2005, 1179-1193. [doi:10.1137/090768539](https://doi.org/10.1137/090768539)

# 示例

```jldoctest
julia> A = Matrix(1.0I, 2, 2)
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0

julia> exp(A)
2×2 Matrix{Float64}:
 2.71828  0.0
 0.0      2.71828
```
