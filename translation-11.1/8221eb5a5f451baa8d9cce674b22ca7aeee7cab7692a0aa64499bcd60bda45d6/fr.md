```
potrs!(uplo, A, B)
```

Trouve la solution de `A * X = B` où `A` est une matrice symétrique ou hermitienne définie positive dont la décomposition de Cholesky a été calculée par `potrf!`. Si `uplo = U`, la décomposition de Cholesky supérieure de `A` a été calculée. Si `uplo = L`, la décomposition de Cholesky inférieure de `A` a été calculée. `B` est écrasé avec la solution `X`.
