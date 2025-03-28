```
unsafe_copyto!(dest::Array, do, src::Array, so, N)
```

Copie `N` éléments d'un tableau source vers un tableau de destination, en commençant à l'index linéaire `so` dans la source et `do` dans la destination (indexé à partir de 1).

Le préfixe `unsafe` sur cette fonction indique qu'aucune validation n'est effectuée pour s'assurer que N est dans les limites des deux tableaux. Une utilisation incorrecte peut corrompre ou provoquer un segfault dans votre programme, de la même manière que C.
