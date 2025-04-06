```
similar(A::AbstractSparseMatrixCSC{Tv,Ti}, [::Type{TvNew}, ::Type{TiNew}, m::Integer, n::Integer]) where {Tv,Ti}
```

Crea un arreglo mutable no inicializado con el tipo de elemento, tipo de índice y tamaño dados, basado en la fuente `SparseMatrixCSC` dada. La nueva matriz dispersa mantiene la estructura de la matriz dispersa original, excepto en el caso en que las dimensiones de la matriz de salida son diferentes de la salida.

La matriz de salida tiene ceros en las mismas ubicaciones que la entrada, pero valores no inicializados para las ubicaciones no nulas.
