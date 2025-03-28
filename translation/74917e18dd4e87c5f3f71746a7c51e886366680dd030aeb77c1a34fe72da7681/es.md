```
RowNonZero
```

El primer elemento no cero en las filas restantes se elige como el elemento pivote.

Ten en cuenta que para matrices de punto flotante, el algoritmo LU resultante es numéricamente inestable; esta estrategia es principalmente útil para la comparación con cálculos manuales (que típicamente utilizan esta estrategia) o para otros tipos algebraicos (por ejemplo, números racionales) que no son susceptibles a errores de redondeo. De lo contrario, la estrategia de pivoteo por defecto `RowMaximum` debería ser generalmente preferida en la eliminación de Gauss.

Ten en cuenta que el [tipo de elemento](@ref eltype) de la matriz debe admitir un método [`iszero`](@ref).
