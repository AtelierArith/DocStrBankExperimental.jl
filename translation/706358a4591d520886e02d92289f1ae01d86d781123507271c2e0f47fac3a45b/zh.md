```
sqrt(A::AbstractMatrix)
```

如果 `A` 没有负的实特征值，计算 `A` 的主矩阵平方根，即唯一的矩阵 $X$，其特征值具有正实部，使得 $X^2 = A$。否则，将返回非主平方根。

如果 `A` 是实对称或厄米矩阵，则使用其特征分解 ([`eigen`](@ref)) 来计算平方根。对于这样的矩阵，由于舍入误差而略微负的特征值 λ 被视为零。更准确地说，所有特征值 `≥ -rtol*(max |λ|)` 的矩阵被视为半正定（产生一个厄米平方根），负特征值被视为零。`rtol` 是 `sqrt` 的一个关键字参数（仅在厄米/实对称情况下），默认为机器精度乘以 `size(A,1)`。

否则，平方根通过 Björck-Hammarling 方法 [^BH83] 确定，该方法计算复 Schur 形式 ([`schur`](@ref))，然后计算三角因子的复平方根。如果存在实平方根，则使用该方法的扩展 [^H87]，该扩展计算实 Schur 形式，然后计算准三角因子的实平方根。

[^BH83]: Åke Björck 和 Sven Hammarling, "A Schur method for the square root of a matrix", Linear Algebra and its Applications, 52-53, 1983, 127-140. [doi:10.1016/0024-3795(83)80010-X](https://doi.org/10.1016/0024-3795(83)80010-X)

[^H87]: Nicholas J. Higham, "Computing real square roots of a real matrix", Linear Algebra and its Applications, 88-89, 1987, 405-430. [doi:10.1016/0024-3795(87)90118-2](https://doi.org/10.1016/0024-3795(87)90118-2)

# 示例

```jldoctest
julia> A = [4 0; 0 4]
2×2 Matrix{Int64}:
 4  0
 0  4

julia> sqrt(A)
2×2 Matrix{Float64}:
 2.0  0.0
 0.0  2.0
```
