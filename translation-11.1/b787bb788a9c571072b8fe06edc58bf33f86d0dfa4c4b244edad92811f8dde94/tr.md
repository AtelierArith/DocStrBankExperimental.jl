```
trmm(side, ul, tA, dA, alpha, A, B)
```

`alpha*A*B` veya [`side`](@ref stdlib-blas-side) ve [`tA`](@ref stdlib-blas-trans) tarafından belirlenen diğer üç varyanttan birini döndürün. Sadece [`ul`](@ref stdlib-blas-uplo) üçgeni `A` kullanılır. [`dA`](@ref stdlib-blas-diag) köşegen değerlerinin okunup okunmayacağını veya hepsinin bir olarak varsayıldığını belirler.
