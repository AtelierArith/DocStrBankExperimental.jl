```
acos(A::AbstractMatrix)
```

计算方阵 `A` 的逆矩阵余弦。

如果 `A` 是对称的或厄米的，则使用其特征分解 ([`eigen`](@ref)) 来计算逆余弦。否则，逆余弦是通过使用 [`log`](@ref) 和 [`sqrt`](@ref) 来确定的。有关用于计算此函数的理论和对数公式，请参见 [^AH16_1]。

[^AH16_1]: Mary Aprahamian 和 Nicholas J. Higham, "矩阵逆三角和逆双曲函数：理论与算法", MIMS EPrint: 2016.4. [https://doi.org/10.1137/16M1057577](https://doi.org/10.1137/16M1057577)

# 示例

```julia-repl
julia> acos(cos([0.5 0.1; -0.2 0.3]))
2×2 Matrix{ComplexF64}:
  0.5-8.32667e-17im  0.1+0.0im
 -0.2+2.63678e-16im  0.3-3.46945e-16im
```
