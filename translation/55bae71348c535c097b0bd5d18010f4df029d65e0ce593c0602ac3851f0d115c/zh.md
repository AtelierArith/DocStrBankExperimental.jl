```
hermitianpart!(A::AbstractMatrix, uplo::Symbol=:U) -> Hermitian
```

就地覆盖方阵 `A` 的厄米部分 `(A + A') / 2`，并返回 [`Hermitian(A, uplo)`](@ref)。对于实矩阵 `A`，这也被称为 `A` 的对称部分。

另请参见 [`hermitianpart`](@ref) 以获取相应的非就地操作。

!!! compat "Julia 1.10"
    此函数需要 Julia 1.10 或更高版本。

