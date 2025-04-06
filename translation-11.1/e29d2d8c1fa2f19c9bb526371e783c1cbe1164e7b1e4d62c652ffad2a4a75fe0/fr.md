```
RowMaximum
```

L'élément de plus grande magnitude dans les lignes restantes est choisi comme élément pivot. C'est la stratégie par défaut pour la factorisation LU des matrices à virgule flottante, et est parfois appelée l'algorithme de "pivotage partiel".

Notez que le [type d'élément](@ref eltype) de la matrice doit admettre une méthode [`abs`](@ref), dont le type de résultat doit admettre une méthode [`<`](@ref).
