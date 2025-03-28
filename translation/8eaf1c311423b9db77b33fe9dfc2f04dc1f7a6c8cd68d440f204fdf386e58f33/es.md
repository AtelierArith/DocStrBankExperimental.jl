```
ldiv!(A::Tridiagonal, B::AbstractVecOrMat) -> B
```

Calcula `A \ B` en su lugar mediante eliminación gaussiana con pivoteo parcial y almacena el resultado en `B`, devolviendo el resultado. En el proceso, las diagonales de `A` se sobrescriben también.

!!! compat "Julia 1.11"
    `ldiv!` para lados izquierdos `Tridiagonal` requiere al menos Julia 1.11.

