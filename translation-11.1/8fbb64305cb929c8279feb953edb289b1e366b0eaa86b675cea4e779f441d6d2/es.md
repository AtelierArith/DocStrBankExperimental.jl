```
getrf!(A) -> (A, ipiv, info)
```

Calcula la factorización `LU` con pivoteo de `A`, `A = LU`.

Devuelve `A`, modificado en su lugar, `ipiv`, la información de pivoteo, y un código `info` que indica éxito (`info = 0`), un valor singular en `U` (`info = i`, en cuyo caso `U[i,i]` es singular), o un código de error (`info < 0`).
