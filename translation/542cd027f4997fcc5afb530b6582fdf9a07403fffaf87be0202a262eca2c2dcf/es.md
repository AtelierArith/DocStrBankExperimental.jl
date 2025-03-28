```
syr2k(uplo, trans, A, B)
```

Devuelve el triángulo [`uplo`](@ref stdlib-blas-uplo) de `A*transpose(B) + B*transpose(A)` o `transpose(A)*B + transpose(B)*A`, según [`trans`](@ref stdlib-blas-trans).
