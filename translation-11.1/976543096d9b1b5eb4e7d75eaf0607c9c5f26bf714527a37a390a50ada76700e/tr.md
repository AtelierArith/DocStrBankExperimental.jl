```
gemmt(uplo, tA, tB, alpha, A, B)
```

`A*B`'nin alt veya üst üçgen kısmını [`uplo`](@ref stdlib-blas-uplo) tarafından belirtilen şekilde döndürür veya [`tA`](@ref stdlib-blas-trans) ve `tB`'ye göre diğer üç varyantı döndürür.

!!! compat "Julia 1.11"
    `gemmt` en az Julia 1.11 gerektirir.

