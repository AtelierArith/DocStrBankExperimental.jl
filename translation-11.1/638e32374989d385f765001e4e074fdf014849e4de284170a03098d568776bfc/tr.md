```
gemmt!(uplo, tA, tB, alpha, A, B, beta, C)
```

`C`'yi [`uplo`](@ref stdlib-blas-uplo) tarafından belirtilen alt veya üst üçgen kısmını `alpha*A*B + beta*C` veya [`tA`](@ref stdlib-blas-trans) ve `tB`'ye göre diğer varyantlar olarak güncelleyin. Güncellenmiş `C`'yi döndürün.

!!! compat "Julia 1.11"
    `gemmt!` en az Julia 1.11 gerektirir.

