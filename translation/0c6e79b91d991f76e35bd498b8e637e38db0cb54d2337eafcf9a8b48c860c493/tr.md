```
syrk(uplo, trans, alpha, A)
```

`A`'n üst üçgenini veya alt üçgenini, [`uplo`](@ref stdlib-blas-uplo) 'ya göre, `alpha*A*transpose(A)` veya `alpha*transpose(A)*A`'yı, [`trans`](@ref stdlib-blas-trans) 'e göre döndürür.
