```
her!(uplo, alpha, x, A)
```

Méthodes uniquement pour les tableaux complexes. Mise à jour de rang 1 de la matrice hermitienne `A` avec le vecteur `x` comme `alpha*x*x' + A`. [`uplo`](@ref stdlib-blas-uplo) contrôle quel triangle de `A` est mis à jour. Renvoie `A`.
