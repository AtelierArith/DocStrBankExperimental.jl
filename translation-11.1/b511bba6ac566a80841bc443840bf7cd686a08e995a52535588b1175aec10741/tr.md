```
her2k!(uplo, trans, alpha, A, B, beta, C)
```

Hermit matris `C`'nin Rank-2k güncellemesi `alpha*A*B' + alpha*B*A' + beta*C` veya `alpha*A'*B + alpha*B'*A + beta*C` olarak [`trans`](@ref stdlib-blas-trans)'e göre yapılır. Skalar `beta` gerçek olmalıdır. Sadece `C`'nin [`uplo`](@ref stdlib-blas-uplo) üçgeni kullanılır. `C` döndürülür.
