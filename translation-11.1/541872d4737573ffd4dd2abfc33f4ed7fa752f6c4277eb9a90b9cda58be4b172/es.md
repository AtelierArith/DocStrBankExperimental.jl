```
ordschur(F::Schur, select::Union{Vector{Bool},BitVector}) -> F::Schur
```

Reordena la factorización de Schur `F` de una matriz `A = Z*T*Z'` de acuerdo con el arreglo lógico `select`, devolviendo el objeto de factorización reordenado `F`. Los valores propios seleccionados aparecen en la diagonal principal de `F.Schur` y las correspondientes columnas principales de `F.vectors` forman una base ortogonal/unitaria del subespacio invariante derecho correspondiente. En el caso real, un par de valores propios conjugados complejos debe ser incluido o excluido en su totalidad a través de `select`.
