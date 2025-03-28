```
intersect!(s::Union{AbstractSet,AbstractVector}, itrs...)
```

Intersectionnez tous les ensembles passés et écrasez `s` avec le résultat. Maintenez l'ordre avec les tableaux.

!!! avertissement
    Le comportement peut être inattendu lorsque tout argument muté partage de la mémoire avec un autre argument.

