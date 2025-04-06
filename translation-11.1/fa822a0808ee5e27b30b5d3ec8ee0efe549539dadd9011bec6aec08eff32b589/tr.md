```
herk!(uplo, trans, alpha, A, beta, C)
```

Sadece karmaşık diziler için yöntemler. Hermit matris `C`'nin sıralı-k güncellemesi `alpha*A*A' + beta*C` veya `alpha*A'*A + beta*C` olarak [`trans`](@ref stdlib-blas-trans)'e göre yapılır. Sadece [`uplo`](@ref stdlib-blas-uplo) üçgeni `C`'nin güncellenir. `C` döner.
