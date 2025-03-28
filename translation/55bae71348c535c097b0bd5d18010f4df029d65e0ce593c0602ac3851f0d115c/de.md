```
hermitianpart!(A::AbstractMatrix, uplo::Symbol=:U) -> Hermitian
```

Überschreibe die quadratische Matrix `A` in-place mit ihrem hermiteschen Teil `(A + A') / 2` und gib [`Hermitian(A, uplo)`](@ref) zurück. Für reelle Matrizen `A` ist dies auch als der symmetrische Teil von `A` bekannt.

Siehe auch [`hermitianpart`](@ref) für die entsprechende Operation außerhalb des Platzes.

!!! compat "Julia 1.10"
    Diese Funktion erfordert Julia 1.10 oder höher.

