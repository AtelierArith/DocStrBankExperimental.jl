```
permutedims!(dest, src, perm)
```

Permute les dimensions du tableau `src` et stocke le résultat dans le tableau `dest`. `perm` est un vecteur spécifiant une permutation de longueur `ndims(src)`. Le tableau préalloué `dest` doit avoir `size(dest) == size(src)[perm]` et est complètement écrasé. Aucune permutation en place n'est supportée et des résultats inattendus se produiront si `src` et `dest` ont des régions de mémoire qui se chevauchent.

Voir aussi [`permutedims`](@ref).
