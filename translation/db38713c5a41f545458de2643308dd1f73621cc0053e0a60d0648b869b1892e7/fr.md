```
gebal!(job, A) -> (ilo, ihi, scale)
```

Équilibrez la matrice `A` avant de calculer son système d'eigenvalues ou sa factorisation de Schur. `job` peut être l'un de `N` (`A` ne sera pas permuté ou mis à l'échelle), `P` (`A` sera seulement permuté), `S` (`A` sera seulement mis à l'échelle), ou `B` (`A` sera à la fois permuté et mis à l'échelle). Modifie `A` sur place et retourne `ilo`, `ihi` et `scale`. Si la permutation a été activée, `A[i,j] = 0` si `j > i` et `1 < j < ilo` ou `j > ihi`. `scale` contient des informations sur les mises à l'échelle/permutations effectuées.
