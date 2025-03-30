```
syrk(uplo, trans, alpha, A)
```

根据 [`uplo`](@ref stdlib-blas-uplo)，返回 `A` 的上三角或下三角，或根据 [`trans`](@ref stdlib-blas-trans) 返回 `alpha*A*transpose(A)` 或 `alpha*transpose(A)*A`。
