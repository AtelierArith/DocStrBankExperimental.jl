```
spr!(uplo, α, x, AP)
```

Mettre à jour la matrice `A` comme `A+α*x*x'`, où `A` est une matrice symétrique fournie au format packagé `AP` et `x` est un vecteur.

Avec `uplo = 'U'`, le tableau AP doit contenir la partie triangulaire supérieure de la matrice symétrique emballée séquentiellement, colonne par colonne, de sorte que `AP[1]` contienne `A[1, 1]`, `AP[2]` et `AP[3]` contiennent respectivement `A[1, 2]` et `A[2, 2]`, et ainsi de suite.

Avec `uplo = 'L'`, le tableau AP doit contenir la partie triangulaire inférieure de la matrice symétrique emballée séquentiellement, colonne par colonne, de sorte que `AP[1]` contienne `A[1, 1]`, `AP[2]` et `AP[3]` contiennent respectivement `A[2, 1]` et `A[3, 1]`, et ainsi de suite.

L'entrée scalaire `α` doit être réelle.

Les entrées de tableau `x` et `AP` doivent toutes être de type `Float32` ou `Float64`. Retournez le `AP` mis à jour.

!!! compat "Julia 1.8"
    `spr!` nécessite au moins Julia 1.8.

