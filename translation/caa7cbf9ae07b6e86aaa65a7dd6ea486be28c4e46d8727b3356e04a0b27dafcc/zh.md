```
opnorm(A::AbstractMatrix, p::Real=2)
```

计算由向量 `p`-范数诱导的算子范数（或矩阵范数），其中有效的 `p` 值为 `1`、`2` 或 `Inf`。（请注意，对于稀疏矩阵，当前未实现 `p=2`。）使用 [`norm`](@ref) 计算 Frobenius 范数。

当 `p=1` 时，算子范数是矩阵 `A` 的最大绝对列和：

$$
\|A\|_1 = \max_{1 ≤ j ≤ n} \sum_{i=1}^m | a_{ij} |
$$

其中 $a_{ij}$ 是矩阵 `A` 的元素，$m$ 和 $n$ 是其维度。

当 `p=2` 时，算子范数是谱范数，等于矩阵 `A` 的最大奇异值。

当 `p=Inf` 时，算子范数是矩阵 `A` 的最大绝对行和：

$$
\|A\|_\infty = \max_{1 ≤ i ≤ m} \sum _{j=1}^n | a_{ij} |
$$

# 示例

```jldoctest
julia> A = [1 -2 -3; 2 3 -1]
2×3 Matrix{Int64}:
 1  -2  -3
 2   3  -1

julia> opnorm(A, Inf)
6.0

julia> opnorm(A, 1)
5.0
```
