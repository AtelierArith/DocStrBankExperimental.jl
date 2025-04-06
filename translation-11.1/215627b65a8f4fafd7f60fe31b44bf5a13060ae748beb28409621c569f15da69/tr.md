```
trsm(side, ul, tA, dA, alpha, A, B)
```

`A*X = alpha*B` çözümünü veya [`side`](@ref stdlib-blas-side) ve [`tA`](@ref stdlib-blas-trans) tarafından belirlenen diğer üç varyanttan birini döndürür. Sadece `A`'nın [`ul`](@ref stdlib-blas-uplo) üçgeni kullanılır. [`dA`](@ref stdlib-blas-diag) köşe değerlerinin okunup okunmayacağını veya hepsinin bir olarak varsayıldığını belirler.
