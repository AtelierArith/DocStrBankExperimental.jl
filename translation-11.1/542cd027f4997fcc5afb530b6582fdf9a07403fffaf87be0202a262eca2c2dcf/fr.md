```
syr2k(uplo, trans, A, B)
```

Retourne le triangle [`uplo`](@ref stdlib-blas-uplo) de `A*transpose(B) + B*transpose(A)` ou `transpose(A)*B + transpose(B)*A`, selon [`trans`](@ref stdlib-blas-trans).
