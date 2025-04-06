```
findmin!(rval, rind, A) -> (minval, index)
```

Trouvez le minimum de `A` et l'indice linéaire correspondant le long des dimensions singleton de `rval` et `rind`, et stockez les résultats dans `rval` et `rind`. `NaN` est considéré comme inférieur à toutes les autres valeurs sauf `missing`.

!!! avertissement
    Le comportement peut être inattendu lorsque tout argument muté partage de la mémoire avec un autre argument.

