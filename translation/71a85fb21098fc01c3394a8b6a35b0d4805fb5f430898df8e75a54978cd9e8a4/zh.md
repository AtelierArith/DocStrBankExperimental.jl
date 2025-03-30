```
gemmt(uplo, tA, tB, A, B)
```

返回由 [`uplo`](@ref stdlib-blas-uplo) 指定的 `A*B` 的下三角或上三角部分，或根据 [`tA`](@ref stdlib-blas-trans) 和 `tB` 的其他三个变体。

!!! compat "Julia 1.11"
    `gemmt` 至少需要 Julia 1.11。

