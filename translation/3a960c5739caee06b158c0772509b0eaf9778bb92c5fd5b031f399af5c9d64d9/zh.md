```
UpperHessenberg(A::AbstractMatrix)
```

构造矩阵 `A` 的 `UpperHessenberg` 视图。`A` 中第一副对角线以下的条目将被忽略。

!!! compat "Julia 1.3"
    此类型在 Julia 1.3 中添加。


为 `H \ b`、`det(H)` 和类似操作实现了高效算法。

另请参见 [`hessenberg`](@ref) 函数，以将任何矩阵分解为类似的上Hessenberg矩阵。

如果 `F::Hessenberg` 是分解对象，则可以通过 `F.Q` 访问单位矩阵，通过 `F.H` 访问Hessenberg矩阵。当提取 `Q` 时，结果类型为 `HessenbergQ` 对象，并且可以通过 [`convert(Array, _)`](@ref)（或简写为 `Array(_)`）转换为常规矩阵。

迭代分解会产生因子 `F.Q` 和 `F.H`。

# 示例

```jldoctest
julia> A = [1 2 3 4; 5 6 7 8; 9 10 11 12; 13 14 15 16]
4×4 Matrix{Int64}:
  1   2   3   4
  5   6   7   8
  9  10  11  12
 13  14  15  16

julia> UpperHessenberg(A)
4×4 UpperHessenberg{Int64, Matrix{Int64}}:
 1   2   3   4
 5   6   7   8
 ⋅  10  11  12
 ⋅   ⋅  15  16
```
