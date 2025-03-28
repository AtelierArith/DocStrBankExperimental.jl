```
syr2k(uplo, trans, alpha, A, B)
```

Gibt das [`uplo`](@ref stdlib-blas-uplo) Dreieck von `alpha*A*transpose(B) + alpha*B*transpose(A)` oder `alpha*transpose(A)*B + alpha*transpose(B)*A` zurück, je nach [`trans`](@ref stdlib-blas-trans).
