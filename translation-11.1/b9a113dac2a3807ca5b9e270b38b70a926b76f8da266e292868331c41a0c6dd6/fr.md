```
syr!(uplo, alpha, x, A)
```

Mise à jour de rang-1 de la matrice symétrique `A` avec le vecteur `x` sous la forme `alpha*x*transpose(x) + A`. [`uplo`](@ref stdlib-blas-uplo) contrôle quel triangle de `A` est mis à jour. Renvoie `A`.
