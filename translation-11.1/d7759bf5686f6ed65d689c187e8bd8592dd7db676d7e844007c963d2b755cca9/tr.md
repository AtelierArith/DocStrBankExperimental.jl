```
sbmv!(uplo, k, alpha, A, x, beta, y)
```

Vektörü `y`'yi `alpha*A*x + beta*y` olarak güncelleyin; burada `A`, `A` argümanında saklanan `k` üst diyagonal ile `size(A,2)` boyutunda simetrik bir bant matristir. `A` için saklama düzeni, [https://www.netlib.org/lapack/explore-html/](https://www.netlib.org/lapack/explore-html/) adresindeki referans BLAS modülünde açıklanmıştır. Sadece [`uplo`](@ref stdlib-blas-uplo) üçgeni `A`'nın kullanılır.

Güncellenmiş `y`'yi döndürün.
