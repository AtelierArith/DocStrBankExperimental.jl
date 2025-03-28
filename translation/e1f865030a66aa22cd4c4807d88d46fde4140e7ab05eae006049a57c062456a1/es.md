```
SparseArrays.spzeros!(::Type{Tv}, I, J, [m, n]) -> SparseMatrixCSC{Tv}
```

Variante de `spzeros!` que reutiliza los vectores de entrada `I` y `J` para el almacenamiento de la matriz final. Después de la construcción, los vectores de entrada harán alias a los búferes de la matriz; `S.colptr === I` y `S.rowval === J` se cumple, y se redimensionarán según sea necesario.

Tenga en cuenta que algunos búferes de trabajo aún se asignarán. Específicamente, este método es un envoltorio de conveniencia alrededor de `spzeros!(Tv, I, J, m, n, klasttouch, csrrowptr, csrcolval, csccolptr, cscrowval)` donde este método asigna `klasttouch`, `csrrowptr` y `csrcolval` del tamaño apropiado, pero reutiliza `I` y `J` para `csccolptr` y `cscrowval`.

Los argumentos `m` y `n` tienen como valores predeterminados `maximum(I)` y `maximum(J)`.

!!! compat "Julia 1.10"
    Este método requiere la versión 1.10 de Julia o posterior.

