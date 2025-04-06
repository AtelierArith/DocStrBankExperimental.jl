```
hseqr!(job, compz, ilo, ihi, H, Z) -> (H, Z, w)
```

Calcule toutes les valeurs propres et (optionnellement) la factorisation de Schur d'une matrice réduite à la forme de Hessenberg. Si `H` est équilibré avec `gebal!`, alors `ilo` et `ihi` sont les sorties de `gebal!`. Sinon, ils doivent être `ilo = 1` et `ihi = size(H,2)`. `tau` contient les réflecteurs élémentaires de la factorisation.
