```
syrk!(uplo, trans, alpha, A, beta, C)
```

Simetrik matris `C`'nin sıralı-k güncellemesi `alpha*A*transpose(A) + beta*C` veya `alpha*transpose(A)*A + beta*C` olarak [`trans`](@ref stdlib-blas-trans)'e göre yapılır. Sadece [`uplo`](@ref stdlib-blas-uplo) üçgeni `C`'de kullanılır. `C` döndürülür.
