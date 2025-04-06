```
sparse_hcat(A...)
```

Concatena a lo largo de la dimensión 2. Devuelve un objeto SparseMatrixCSC.

!!! compat "Julia 1.8"
    Este método se agregó en Julia 1.8. Imita el comportamiento de concatenación anterior, donde la concatenación con tipos de matriz "sparse" especializados de LinearAlgebra.jl producía automáticamente una salida dispersa incluso en ausencia de cualquier argumento SparseArray.

