```
posv!(uplo, A, B) -> (A, B)
```

Trouve la solution de `A * X = B` où `A` est une matrice symétrique ou hermitienne définie positive. Si `uplo = U`, la décomposition de Cholesky supérieure de `A` est calculée. Si `uplo = L`, la décomposition de Cholesky inférieure de `A` est calculée. `A` est écrasée par sa décomposition de Cholesky. `B` est écrasé avec la solution `X`.
