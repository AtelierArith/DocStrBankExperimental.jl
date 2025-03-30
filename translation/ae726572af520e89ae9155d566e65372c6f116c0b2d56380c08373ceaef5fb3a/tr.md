```
syr2k(uplo, trans, alpha, A, B)
```

[`uplo`](@ref stdlib-blas-uplo) üçgenini `alpha*A*transpose(B) + alpha*B*transpose(A)` veya `alpha*transpose(A)*B + alpha*transpose(B)*A` olarak döndürür, bu `trans`'a göre belirlenir. [`trans`](@ref stdlib-blas-trans).
