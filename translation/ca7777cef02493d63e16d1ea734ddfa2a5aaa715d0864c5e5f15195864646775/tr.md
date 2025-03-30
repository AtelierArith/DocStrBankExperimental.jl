```
trsv!(ul, tA, dA, A, b)
```

`A*x = b` denkleminin çözümü veya [`tA`](@ref stdlib-blas-trans) ve [`ul`](@ref stdlib-blas-uplo) tarafından belirlenen diğer iki varyanttan biri ile `b`'yi güncelleyin. [`dA`](@ref stdlib-blas-diag) köşegen değerlerinin okunup okunmadığını veya hepsinin bir olarak varsayıldığını belirler. Güncellenmiş `b`'yi döndürün.
