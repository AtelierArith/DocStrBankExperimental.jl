```
RowMaximum
```

El elemento de máxima magnitud en las filas restantes se elige como el elemento pivote. Esta es la estrategia predeterminada para la factorización LU de matrices de punto flotante, y a veces se refiere como el algoritmo de "pivoteo parcial".

Tenga en cuenta que el [tipo de elemento](@ref eltype) de la matriz debe admitir un método [`abs`](@ref), cuyo tipo de resultado debe admitir un método [`<`](@ref).
