```
gemmt!(uplo, tA, tB, alpha, A, B, beta, C)
```

Aktualisiert den unteren oder oberen dreieckigen Teil, der durch [`uplo`](@ref stdlib-blas-uplo) von `C` angegeben ist, als `alpha*A*B + beta*C` oder die anderen Varianten gemäß [`tA`](@ref stdlib-blas-trans) und `tB`. Gibt das aktualisierte `C` zurück.

!!! compat "Julia 1.11"
    `gemmt!` erfordert mindestens Julia 1.11.

