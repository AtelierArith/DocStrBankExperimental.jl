```
hemv!(ul, alpha, A, x, beta, y)
```

Vektörü `y`'yi `alpha*A*x + beta*y` olarak güncelleyin. `A`'nın Hermitiyen olduğu varsayılmaktadır. Sadece [`ul`](@ref stdlib-blas-uplo) üçgeni `A`'nın kullanılır. `alpha` ve `beta` skalarlardır. Güncellenmiş `y`'yi döndürün.
