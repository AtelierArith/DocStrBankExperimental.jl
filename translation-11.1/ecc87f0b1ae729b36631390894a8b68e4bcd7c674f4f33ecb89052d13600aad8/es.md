```
SparseArrays.sparse!(I, J, V, [m, n, combine]) -> SparseMatrixCSC
```

Variante de `sparse!` que reutiliza los vectores de entrada (`I`, `J`, `V`) para el almacenamiento de la matriz final. Después de la construcción, los vectores de entrada harán alias a los búferes de la matriz; `S.colptr === I`, `S.rowval === J`, y `S.nzval === V` se cumple, y se redimensionarán según sea necesario.

Tenga en cuenta que algunos búferes de trabajo aún se asignarán. Específicamente, este método es un envoltorio de conveniencia alrededor de `sparse!(I, J, V, m, n, combine, klasttouch, csrrowptr, csrcolval, csrnzval, csccolptr, cscrowval, cscnzval)` donde este método asigna `klasttouch`, `csrrowptr`, `csrcolval`, y `csrnzval` de tamaño apropiado, pero reutiliza `I`, `J`, y `V` para `csccolptr`, `cscrowval`, y `cscnzval`.

Los argumentos `m`, `n`, y `combine` tienen como valores predeterminados `maximum(I)`, `maximum(J)`, y `+`, respectivamente.

!!! compat "Julia 1.10"
    Este método requiere Julia versión 1.10 o posterior.

