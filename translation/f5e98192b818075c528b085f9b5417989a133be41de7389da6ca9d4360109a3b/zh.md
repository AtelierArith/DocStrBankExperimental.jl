```
hermitianpart(A::AbstractMatrix, uplo::Symbol=:U) -> Hermitian
```

返回方阵 `A` 的厄米部分，定义为 `(A + A') / 2`，作为一个 [`Hermitian`](@ref) 矩阵。对于实矩阵 `A`，这也被称为 `A` 的对称部分；有时也称为“算子实部”。可选参数 `uplo` 控制 [`Hermitian`](@ref) 视图的相应参数。对于实矩阵，后者等同于 [`Symmetric`](@ref) 视图。

另请参见 [`hermitianpart!`](@ref) 以获取相应的就地操作。

!!! compat "Julia 1.10"
    此函数需要 Julia 1.10 或更高版本。

