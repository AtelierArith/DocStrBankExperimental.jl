```
syr2k!(uplo, trans, alpha, A, B, beta, C)
```

Simetrik matris `C`'nin rank-2k güncellemesi `alpha*A*transpose(B) + alpha*B*transpose(A) + beta*C` veya `alpha*transpose(A)*B + alpha*transpose(B)*A + beta*C` olarak [`trans`](@ref stdlib-blas-trans)'e göre yapılır. Sadece [`uplo`](@ref stdlib-blas-uplo) üçgeni `C`'de kullanılır. `C` döner.
