```
symm!(side, ul, alpha, A, B, beta, C)
```

`C`'yi `alpha*A*B + beta*C` veya `alpha*B*A + beta*C` olarak güncelleyin, [`side`](@ref stdlib-blas-side)'a göre. `A`'nın simetrik olduğu varsayılmaktadır. Sadece `A`'nın [`ul`](@ref stdlib-blas-uplo) üçgeni kullanılır. Güncellenmiş `C`'yi döndürün.
