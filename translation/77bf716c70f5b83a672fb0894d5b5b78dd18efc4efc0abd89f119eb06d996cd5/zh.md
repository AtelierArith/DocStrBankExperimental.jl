```
asin(A::AbstractMatrix)
```

计算方阵 `A` 的逆矩阵正弦。

如果 `A` 是对称的或厄米的，则使用其特征分解 ([`eigen`](@ref)) 来计算逆正弦。否则，逆正弦是通过使用 [`log`](@ref) 和 [`sqrt`](@ref) 来确定的。有关用于计算此函数的理论和对数公式，请参见 [^AH16_2]。

[^AH16_2]: Mary Aprahamian 和 Nicholas J. Higham, "矩阵逆三角函数和逆双曲函数：理论与算法", MIMS EPrint: 2016.4. [https://doi.org/10.1137/16M1057577](https://doi.org/10.1137/16M1057577)

# 示例

```julia-repl
julia> asin(sin([0.5 0.1; -0.2 0.3]))
2×2 Matrix{ComplexF64}:
  0.5-4.16334e-17im  0.1-5.55112e-17im
 -0.2+9.71445e-17im  0.3-1.249e-16im
```
