```
syrk(uplo, trans, alpha, A)
```

Gibt entweder das obere Dreieck oder das untere Dreieck von `A` zurück, entsprechend [`uplo`](@ref stdlib-blas-uplo), von `alpha*A*transpose(A)` oder `alpha*transpose(A)*A`, entsprechend [`trans`](@ref stdlib-blas-trans).
