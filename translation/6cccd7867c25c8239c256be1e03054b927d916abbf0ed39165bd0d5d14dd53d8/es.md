```
spzeros([tipo], I::AbstractVector, J::AbstractVector, [m, n])
```

Crea una matriz dispersa `S` de dimensiones `m x n` con ceros estructurales en `S[I[k], J[k]]`.

Este método se puede utilizar para construir el patrón de dispersidad de la matriz, y es más eficiente que usar, por ejemplo, `sparse(I, J, zeros(length(I)))`.

Para documentación adicional y un controlador experto, consulta `SparseArrays.spzeros!`.

!!! compat "Julia 1.10"
    Este método requiere la versión 1.10 de Julia o posterior.

