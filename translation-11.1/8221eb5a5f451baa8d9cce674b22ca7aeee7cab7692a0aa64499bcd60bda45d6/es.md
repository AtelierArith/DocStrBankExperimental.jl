```
potrs!(uplo, A, B)
```

Encuentra la solución a `A * X = B` donde `A` es una matriz simétrica o hermítica definida positiva cuya descomposición de Cholesky fue calculada por `potrf!`. Si `uplo = U`, se calculó la descomposición de Cholesky superior de `A`. Si `uplo = L`, se calculó la descomposición de Cholesky inferior de `A`. `B` se sobrescribe con la solución `X`.
