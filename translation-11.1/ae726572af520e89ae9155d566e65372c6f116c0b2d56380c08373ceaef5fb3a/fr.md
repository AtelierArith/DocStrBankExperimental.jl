```
syr2k(uplo, trans, alpha, A, B)
```

Renvoie le triangle [`uplo`](@ref stdlib-blas-uplo) de `alpha*A*transpose(B) + alpha*B*transpose(A)` ou `alpha*transpose(A)*B + alpha*transpose(B)*A`, selon [`trans`](@ref stdlib-blas-trans).
