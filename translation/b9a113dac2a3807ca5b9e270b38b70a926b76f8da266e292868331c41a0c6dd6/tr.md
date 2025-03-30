```
syr!(uplo, alpha, x, A)
```

Simetrik matris `A`'nın sıralı güncellemesi `alpha*x*transpose(x) + A` ile `x` vektörü kullanılarak yapılır. [`uplo`](@ref stdlib-blas-uplo) `A`'nın hangi üçgeninin güncelleneceğini kontrol eder. `A` döner.
