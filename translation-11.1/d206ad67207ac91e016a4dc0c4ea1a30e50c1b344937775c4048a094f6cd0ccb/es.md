```
getrf!(A, ipiv) -> (A, ipiv, info)
```

Calcula la factorización `LU` con pivoteo de `A`, `A = LU`. `ipiv` contiene la información de pivoteo y `info` un código que indica éxito (`info = 0`), un valor singular en `U` (`info = i`, en cuyo caso `U[i,i]` es singular), o un código de error (`info < 0`).
