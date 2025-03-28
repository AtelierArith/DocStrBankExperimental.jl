```
cholesky!(A::AbstractMatrix, RowMaximum(); tol = 0.0, check = true) -> CholeskyPivoted
```

Lo mismo que [`cholesky`](@ref), pero ahorra espacio al sobrescribir la entrada `A`, en lugar de crear una copia. Se lanza una excepción [`InexactError`](@ref) si la factorización produce un número que no es representable por el tipo de elemento de `A`, por ejemplo, para tipos enteros.
