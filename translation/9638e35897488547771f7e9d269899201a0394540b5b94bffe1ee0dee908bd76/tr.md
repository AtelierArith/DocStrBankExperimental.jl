```
trmm!(taraf, ul, tA, dA, alpha, A, B)
```

`B`'yi `alpha*A*B` veya [`side`](@ref stdlib-blas-side) ve [`tA`](@ref stdlib-blas-trans) tarafından belirlenen diğer üç varyanttan biri ile güncelleyin. Sadece [`ul`](@ref stdlib-blas-uplo) üçgeni `A`'nın kullanılır. [`dA`](@ref stdlib-blas-diag) köşegen değerlerinin okunup okunmayacağını veya hepsinin bir olarak varsayıldığını belirler. Güncellenmiş `B`'yi döndürün.
