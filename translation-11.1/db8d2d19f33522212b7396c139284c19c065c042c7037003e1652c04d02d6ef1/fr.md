```
symdiff!(s::Union{AbstractSet,AbstractVector}, itrs...)
```

Construit la différence symétrique des ensembles passés en paramètres et écrase `s` avec le résultat. Lorsque `s` est un tableau, l'ordre est maintenu. Notez que dans ce cas, la multiplicité des éléments est importante.

!!! avertissement
    Le comportement peut être inattendu lorsque tout argument muté partage de la mémoire avec un autre argument.

