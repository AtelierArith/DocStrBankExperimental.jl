```
trexc!(compq, ifst, ilst, T, Q) -> (T, Q)
trexc!(ifst, ilst, T, Q) -> (T, Q)
```

Reordena la factorización de Schur `T` de una matriz, de modo que el bloque diagonal de `T` con índice de fila `ifst` se mueva al índice de fila `ilst`. Si `compq = V`, los vectores de Schur `Q` se reordenan. Si `compq = N`, no se modifican. El método de 4 argumentos llama al método de 5 argumentos con `compq = V`.
