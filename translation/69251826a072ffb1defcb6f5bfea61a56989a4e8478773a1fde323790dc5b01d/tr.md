```
gemv!(tA, alpha, A, x, beta, y)
```

Vektörü `y`'yi `alpha*A*x + beta*y` veya `alpha*A'x + beta*y` olarak günceller. [`tA`](@ref stdlib-blas-trans) ile ilgili olarak. `alpha` ve `beta` skalarlardır. Güncellenmiş `y`'yi döndür.
