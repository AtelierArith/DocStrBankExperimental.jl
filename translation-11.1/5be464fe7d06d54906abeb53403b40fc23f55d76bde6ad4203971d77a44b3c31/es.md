```
sparse_hvcat(rows::Tuple{Vararg{Int}}, values...)
```

Concatenación horizontal y vertical dispersa en una sola llamada. Esta función se llama para la sintaxis de matrices en bloques. El primer argumento especifica el número de argumentos a concatenar en cada fila de bloque.

!!! compat "Julia 1.8"
    Este método se agregó en Julia 1.8. Imita el comportamiento de concatenación anterior, donde la concatenación con tipos de matrices "dispersas" especializados de LinearAlgebra.jl producía automáticamente una salida dispersa incluso en ausencia de cualquier argumento SparseArray.

