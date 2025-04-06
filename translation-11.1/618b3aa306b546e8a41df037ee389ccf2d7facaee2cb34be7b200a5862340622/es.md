```
gels!(trans, A, B) -> (F, B, ssr)
```

Resuelve la ecuación lineal `A * X = B`, `transpose(A) * X = B` o `adjoint(A) * X = B` utilizando una factorización QR o LQ. Modifica la matriz/vector `B` en su lugar con la solución. `A` se sobrescribe con su factorización `QR` o `LQ`. `trans` puede ser uno de `N` (sin modificación), `T` (transpuesta) o `C` (transpuesta conjugada). `gels!` busca la solución de mínimo norma/mínimos cuadrados. `A` puede estar subdeterminado o sobredeterminado. La solución se devuelve en `B`.
