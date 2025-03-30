```
trsm!(side, ul, tA, dA, alpha, A, B)
```

`B`'yi `A*X = alpha*B` çözümü ile veya [`side`](@ref stdlib-blas-side) ve [`tA`](@ref stdlib-blas-trans) tarafından belirlenen diğer üç varyanttan biri ile güncelleyiniz. Sadece `A`'nın [`ul`](@ref stdlib-blas-uplo) üçgeni kullanılır. [`dA`](@ref stdlib-blas-diag) diyagonal değerlerin okunup okunmayacağını veya hepsinin birer birer varsayıldığını belirler. Güncellenmiş `B`'yi döndürür.
