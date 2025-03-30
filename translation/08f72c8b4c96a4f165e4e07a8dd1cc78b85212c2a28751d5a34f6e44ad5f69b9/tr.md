```
sbmv(uplo, k, A, x)
```

`A*x` döndürür; burada `A`, argüman `A`'da saklanan `k` üst-diagonal ile `size(A,2)` boyutunda bir simetrik bant matrisidir. Sadece [`uplo`](@ref stdlib-blas-uplo) üçgeni kullanılır.
