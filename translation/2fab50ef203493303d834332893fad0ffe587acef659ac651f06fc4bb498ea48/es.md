```
lowrankdowndate!(C::Cholesky, v::AbstractVector) -> CC::Cholesky
```

Realiza una actualización descendente de una factorización de Cholesky `C` con el vector `v`. Si `A = C.U'C.U` entonces `CC = cholesky(C.U'C.U - v*v')` pero el cálculo de `CC` solo utiliza `O(n^2)` operaciones. La factorización de entrada `C` se actualiza en su lugar de tal manera que al salir `C == CC`. El vector `v` se destruye durante el cálculo.
