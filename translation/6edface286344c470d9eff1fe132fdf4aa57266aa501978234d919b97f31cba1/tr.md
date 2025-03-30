```
hemm!(side, ul, alpha, A, B, beta, C)
```

`C`'yi `alpha*A*B + beta*C` veya `alpha*B*A + beta*C` olarak güncelleyin, bu [`side`](@ref stdlib-blas-side)'a göre. `A`'nın Hermitian olduğu varsayılmaktadır. Sadece `A`'nın [`ul`](@ref stdlib-blas-uplo) üçgeni kullanılır. Güncellenmiş `C`'yi döndürün.
