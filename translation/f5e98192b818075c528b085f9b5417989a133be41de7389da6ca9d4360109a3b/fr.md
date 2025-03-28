```
hermitianpart(A::AbstractMatrix, uplo::Symbol=:U) -> Hermitian
```

Retourne la partie hermitienne de la matrice carrée `A`, définie comme `(A + A') / 2`, sous forme d'une matrice [`Hermitian`](@ref). Pour les matrices réelles `A`, cela est également connu sous le nom de partie symétrique de `A` ; on l'appelle parfois la "partie réelle de l'opérateur". L'argument optionnel `uplo` contrôle l'argument correspondant de la vue [`Hermitian`](@ref). Pour les matrices réelles, cette dernière est équivalente à une vue [`Symmetric`](@ref).

Voir aussi [`hermitianpart!`](@ref) pour l'opération correspondante en place.

!!! compat "Julia 1.10"
    Cette fonction nécessite Julia 1.10 ou une version ultérieure.

