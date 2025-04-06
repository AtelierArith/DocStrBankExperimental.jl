```
gbmv!(trans, m, kl, ku, alpha, A, x, beta, y)
```

Vektörü `y`'yi `alpha*A*x + beta*y` veya `alpha*A'*x + beta*y` olarak güncelleyin, [`trans`](@ref stdlib-blas-trans) ile ilgili olarak. Matris `A`, `kl` alt-diagonal ve `ku` üst-diagonal ile `m` boyutunda ve `size(A,2)` boyutunda genel bir bant matristir. `alpha` ve `beta` skalarlardır. Güncellenmiş `y`'yi döndürün.
