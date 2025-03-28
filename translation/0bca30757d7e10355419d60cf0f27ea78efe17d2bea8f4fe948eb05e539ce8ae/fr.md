```
unsafe_copyto!(dest::Ptr{T}, src::Ptr{T}, N)
```

Copie `N` éléments d'un pointeur source vers une destination, sans vérification. La taille d'un élément est déterminée par le type des pointeurs.

Le préfixe `unsafe` sur cette fonction indique qu'aucune validation n'est effectuée sur les pointeurs `dest` et `src` pour s'assurer qu'ils sont valides. Une utilisation incorrecte peut corrompre ou provoquer un segfault dans votre programme, de la même manière qu'en C.
