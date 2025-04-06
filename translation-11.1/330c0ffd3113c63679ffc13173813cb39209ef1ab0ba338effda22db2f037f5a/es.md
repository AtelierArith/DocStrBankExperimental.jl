```
ColumnNorm
```

La columna con la norma máxima se utiliza para el cálculo subsiguiente. Esto se utiliza para la factorización QR con pivoteo.

Tenga en cuenta que el [tipo de elemento](@ref eltype) de la matriz debe admitir los métodos [`norm`](@ref) y [`abs`](@ref), cuyos tipos de resultado respectivos deben admitir un método [`<`](@ref).
