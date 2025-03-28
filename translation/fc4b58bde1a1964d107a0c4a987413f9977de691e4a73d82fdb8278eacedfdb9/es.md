```
ZeroPivotException <: Exception
```

Excepción lanzada cuando una factorización/resolución de matriz encuentra un cero en una posición de pivote (diagonal) y no puede continuar. Esto *no* significa necesariamente que la matriz sea singular: puede ser útil cambiar a una factorización diferente, como LU con pivoteo, que puede reordenar variables para eliminar pivotes cero espurios. El campo `info` indica la ubicación de (uno de) los pivotes cero.
