```
ColumnNorm
```

La colonne avec la norme maximale est utilisée pour les calculs ultérieurs. Cela est utilisé pour la factorisation QR pivotée.

Notez que le [type d'élément](@ref eltype) de la matrice doit admettre les méthodes [`norm`](@ref) et [`abs`](@ref), dont les types de résultats respectifs doivent admettre une méthode [`<`](@ref).
