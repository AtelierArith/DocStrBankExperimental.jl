```
syconv!(uplo, A, ipiv) -> (A, work)
```

Convierte una matriz simétrica `A` (que ha sido factorizada en una matriz triangular) en dos matrices `L` y `D`. Si `uplo = U`, `A` es triangular superior. Si `uplo = L`, es triangular inferior. `ipiv` es el vector de pivote de la factorización triangular. `A` se sobrescribe con `L` y `D`.
