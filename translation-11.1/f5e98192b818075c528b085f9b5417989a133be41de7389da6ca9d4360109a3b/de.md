```
hermitianpart(A::AbstractMatrix, uplo::Symbol=:U) -> Hermitian
```

Gibt den hermiteschen Teil der quadratischen Matrix `A` zurück, definiert als `(A + A') / 2`, als [`Hermitian`](@ref) Matrix. Für reelle Matrizen `A` ist dies auch als der symmetrische Teil von `A` bekannt; es wird auch manchmal als der "operatorielle reale Teil" bezeichnet. Das optionale Argument `uplo` steuert das entsprechende Argument der [`Hermitian`](@ref) Ansicht. Für reelle Matrizen ist letzteres äquivalent zu einer [`Symmetric`](@ref) Ansicht.

Siehe auch [`hermitianpart!`](@ref) für die entsprechende In-Place-Operation.

!!! compat "Julia 1.10"
    Diese Funktion erfordert Julia 1.10 oder höher.

