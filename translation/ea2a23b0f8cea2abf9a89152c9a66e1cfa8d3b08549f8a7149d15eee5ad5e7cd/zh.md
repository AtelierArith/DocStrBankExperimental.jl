```
her2k(uplo, trans, alpha, A, B)
```

返回 [`uplo`](@ref stdlib-blas-uplo) 三角形的 `alpha*A*B' + alpha*B*A'` 或 `alpha*A'*B + alpha*B'*A`，具体取决于 [`trans`](@ref stdlib-blas-trans)。
