```
sbmv(uplo, k, alpha, A, x)
```

`alpha*A*x` döndürür; burada `A`, `A` argümanında saklanan `k` üst-diagonal ile `size(A,2)` boyutunda bir simetrik bant matrisidir. Sadece [`uplo`](@ref stdlib-blas-uplo) üçgeni kullanılır.
