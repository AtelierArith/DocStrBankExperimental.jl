```
RowNonZero
```

Le premier élément non nul dans les lignes restantes est choisi comme élément pivot.

Attention, pour les matrices à virgule flottante, l'algorithme LU résultant est numériquement instable — cette stratégie est principalement utile pour la comparaison avec des calculs manuels (qui utilisent généralement cette stratégie) ou pour d'autres types algébriques (par exemple, les nombres rationnels) non susceptibles d'erreurs d'arrondi. Sinon, la stratégie de pivotement par défaut `RowMaximum` devrait généralement être préférée dans l'élimination de Gauss.

Notez que le [type d'élément](@ref eltype) de la matrice doit admettre une méthode [`iszero`](@ref).
