```
lowrankupdate(C::Cholesky, v::AbstractVector) -> CC::Cholesky
```

Actualiza una factorización de Cholesky `C` con el vector `v`. Si `A = C.U'C.U` entonces `CC = cholesky(C.U'C.U + v*v')` pero el cálculo de `CC` solo utiliza `O(n^2)` operaciones.
