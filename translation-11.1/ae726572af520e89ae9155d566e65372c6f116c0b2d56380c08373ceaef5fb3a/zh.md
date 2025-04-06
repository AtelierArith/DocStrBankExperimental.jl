```
syr2k(uplo, trans, alpha, A, B)
```

返回 [`uplo`](@ref stdlib-blas-uplo) 三角形的 `alpha*A*transpose(B) + alpha*B*transpose(A)` 或 `alpha*transpose(A)*B + alpha*transpose(B)*A`，具体取决于 [`trans`](@ref stdlib-blas-trans)。
