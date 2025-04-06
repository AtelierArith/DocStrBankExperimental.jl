```
TriFusion
```

Indiquez qu'une fonction de tri doit utiliser l'algorithme de tri fusion. Le tri fusion divise la collection en sous-collections et les fusionne de manière répétée, triant chaque sous-collection à chaque étape, jusqu'à ce que l'ensemble de la collection ait été recombiné sous forme triée.

Caractéristiques :

  * *stable* : préserve l'ordre des éléments qui se comparent comme égaux (par exemple, "a" et "A" dans un tri de lettres qui ignore la casse).
  * *pas en place* en mémoire.
  * *stratégie de tri* diviser et conquérir.
  * *bonne performance* pour de grandes collections mais généralement pas aussi rapide que [`QuickSort`](@ref).
