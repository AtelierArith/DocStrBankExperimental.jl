```
syr2k(uplo, trans, A, B)
```

返回 [`uplo`](@ref stdlib-blas-uplo) 三角形的 `A*transpose(B) + B*transpose(A)` 或 `transpose(A)*B + transpose(B)*A`，具体取决于 [`trans`](@ref stdlib-blas-trans)。
