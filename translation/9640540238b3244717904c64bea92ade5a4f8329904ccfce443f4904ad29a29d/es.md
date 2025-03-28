```
cholesky!(F::CHOLMOD.Factor, A::SparseMatrixCSC; shift = 0.0, check = true) -> CHOLMOD.Factor
```

Calcula la factorización de Cholesky ($LL'$) de `A`, reutilizando la factorización simbólica `F`. `A` debe ser una [`SparseMatrixCSC`](@ref) o una vista [`Symmetric`](@ref)/ [`Hermitian`](@ref) de una `SparseMatrixCSC`. Ten en cuenta que, incluso si `A` no tiene la etiqueta de tipo, debe seguir siendo simétrica o hermitiana.

Consulta también [`cholesky`](@ref).

!!! nota
    Este método utiliza la biblioteca CHOLMOD de SuiteSparse, que solo admite tipos reales o complejos en precisión simple o doble. Las matrices de entrada que no sean de esos tipos de elemento se convertirán a estos tipos según sea apropiado.

