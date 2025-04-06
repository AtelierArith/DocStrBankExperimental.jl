```
circshift!(dest, src, shifts)
```

Effectuer un décalage circulaire, c'est-à-dire une rotation, des données dans `src`, en stockant le résultat dans `dest`. `shifts` spécifie le montant à décaler dans chaque dimension.

!!! warning
    Le comportement peut être inattendu lorsque tout argument muté partage de la mémoire avec un autre argument.


Voir aussi [`circshift`](@ref).
