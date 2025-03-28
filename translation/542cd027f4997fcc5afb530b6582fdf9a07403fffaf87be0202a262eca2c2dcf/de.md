```
syr2k(uplo, trans, A, B)
```

Gibt das [`uplo`](@ref stdlib-blas-uplo) Dreieck von `A*transpose(B) + B*transpose(A)` oder `transpose(A)*B + transpose(B)*A` zurück, je nach [`trans`](@ref stdlib-blas-trans).
