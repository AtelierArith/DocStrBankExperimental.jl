```
findmax!(rval, rind, A) -> (maxval, index)
```

Trouvez le maximum de `A` et l'indice linéaire correspondant le long des dimensions singleton de `rval` et `rind`, et stockez les résultats dans `rval` et `rind`. `NaN` est considéré comme supérieur à toutes les autres valeurs sauf `missing`.

!!! warning
    Le comportement peut être inattendu lorsque tout argument muté partage de la mémoire avec un autre argument.

