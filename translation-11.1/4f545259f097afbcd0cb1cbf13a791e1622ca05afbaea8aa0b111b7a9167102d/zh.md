```
atan(A::AbstractMatrix)
```

计算方阵 `A` 的逆矩阵正切。

如果 `A` 是对称或厄米矩阵，则使用其特征分解 ([`eigen`](@ref)) 来计算逆正切。否则，逆正切通过使用 [`log`](@ref) 来确定。有关用于计算此函数的理论和对数公式，请参见 [^AH16_3]。

[^AH16_3]: Mary Aprahamian 和 Nicholas J. Higham, "矩阵逆三角和逆双曲函数：理论与算法", MIMS EPrint: 2016.4. [https://doi.org/10.1137/16M1057577](https://doi.org/10.1137/16M1057577)

# 示例

```julia-repl
julia> atan(tan([0.5 0.1; -0.2 0.3]))
2×2 Matrix{ComplexF64}:
  0.5+1.38778e-17im  0.1-2.77556e-17im
 -0.2+6.93889e-17im  0.3-4.16334e-17im
```
