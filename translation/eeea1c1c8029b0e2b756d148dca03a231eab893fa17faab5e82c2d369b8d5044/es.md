```
SparseVector{Tv,Ti<:Integer} <: AbstractSparseVector{Tv,Ti}
```

Tipo de vector para almacenar vectores dispersos. Se puede crear pasando la longitud del vector, un vector *ordenado* de índices no cero y un vector de valores no cero.

Por ejemplo, el vector `[5, 6, 0, 7]` se puede representar como

```julia
SparseVector(4, [1, 2, 4], [5, 6, 7])
```

Esto indica que el elemento en el índice 1 es 5, en el índice 2 es 6, en el índice 3 es `zero(Int)`, y en el índice 4 es 7.

Puede ser más conveniente crear vectores dispersos directamente a partir de vectores densos usando `sparse` como

```julia
sparse([5, 6, 0, 7])
```

produce el mismo vector disperso.
