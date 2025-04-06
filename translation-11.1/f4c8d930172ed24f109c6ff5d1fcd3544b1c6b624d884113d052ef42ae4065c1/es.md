```
posv!(uplo, A, B) -> (A, B)
```

Encuentra la solución a `A * X = B` donde `A` es una matriz simétrica o hermítica definida positiva. Si `uplo = U`, se calcula la descomposición de Cholesky superior de `A`. Si `uplo = L`, se calcula la descomposición de Cholesky inferior de `A`. `A` se sobrescribe con su descomposición de Cholesky. `B` se sobrescribe con la solución `X`.
