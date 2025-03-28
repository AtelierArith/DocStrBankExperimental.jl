```
getri!(A, ipiv)
```

Calcula la inversa de `A`, utilizando su factorización `LU` encontrada por `getrf!`. `ipiv` es la información de pivoteo de salida y `A` contiene la factorización `LU` de `getrf!`. `A` se sobrescribe con su inversa.
