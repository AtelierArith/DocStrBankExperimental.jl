```
gemmt(uplo, tA, tB, alpha, A, B)
```

Gibt den unteren oder oberen dreieckigen Teil an, der durch [`uplo`](@ref stdlib-blas-uplo) von `A*B` oder den anderen drei Varianten gemäß [`tA`](@ref stdlib-blas-trans) und `tB` angegeben ist.

!!! compat "Julia 1.11"
    `gemmt` erfordert mindestens Julia 1.11.

