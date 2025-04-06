```
schur!(A::StridedMatrix, B::StridedMatrix) -> F::GeneralizedSchur
```

Igual que [`schur`](@ref) pero utiliza las matrices de entrada `A` y `B` como espacio de trabajo.
