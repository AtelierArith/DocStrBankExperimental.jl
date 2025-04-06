```
schur!(A::StridedMatrix, B::StridedMatrix) -> F::GeneralizedSchur
```

Identique à [`schur`](@ref) mais utilise les matrices d'entrée `A` et `B` comme espace de travail.
