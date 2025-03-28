```
hermitianpart!(A::AbstractMatrix, uplo::Symbol=:U) -> Hermitian
```

Écrasez la matrice carrée `A` sur place avec sa partie hermitienne `(A + A') / 2`, et retournez [`Hermitian(A, uplo)`](@ref). Pour les matrices réelles `A`, cela est également connu sous le nom de partie symétrique de `A`.

Voir aussi [`hermitianpart`](@ref) pour l'opération correspondante hors place.

!!! compat "Julia 1.10"
    Cette fonction nécessite Julia 1.10 ou une version ultérieure.

