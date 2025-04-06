```
Symmetric(A::AbstractMatrix, uplo::Symbol=:U)
```

构造矩阵 `A` 的上三角（如果 `uplo = :U`）或下三角（如果 `uplo = :L`）的 `Symmetric` 视图。

`Symmetric` 视图主要用于实对称矩阵，对于这些矩阵，专门的算法（例如特征问题）可以为 `Symmetric` 类型启用。更一般地，参见 [`Hermitian(A)`](@ref) 用于厄米矩阵 `A == A'`，这在实矩阵中实际上等同于 `Symmetric`，但对于复矩阵也很有用。（而复 `Symmetric` 矩阵受到支持，但几乎没有任何专门的算法。）

要计算实矩阵的对称部分，或更一般地，实或复矩阵 `A` 的厄米部分 `(A + A') / 2`，请使用 [`hermitianpart`](@ref)。

# 示例

```jldoctest
julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> Supper = Symmetric(A)
3×3 Symmetric{Int64, Matrix{Int64}}:
 1  2  3
 2  5  6
 3  6  9

julia> Slower = Symmetric(A, :L)
3×3 Symmetric{Int64, Matrix{Int64}}:
 1  4  7
 4  5  8
 7  8  9

julia> hermitianpart(A)
3×3 Hermitian{Float64, Matrix{Float64}}:
 1.0  3.0  5.0
 3.0  5.0  7.0
 5.0  7.0  9.0
```

请注意，除非 `A` 本身是对称的（例如，如果 `A == transpose(A)`），否则 `Supper` 将不等于 `Slower`。
