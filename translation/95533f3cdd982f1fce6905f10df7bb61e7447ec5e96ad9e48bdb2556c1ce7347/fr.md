```
rethrow()
```

Relance l'exception actuelle depuis un bloc `catch`. L'exception relancée continuera sa propagation comme si elle n'avait pas été interceptée.

!!! note
    La forme alternative `rethrow(e)` vous permet d'associer un objet d'exception alternatif `e` avec la trace de pile actuelle. Cependant, cela déforme l'état du programme au moment de l'erreur, donc il est conseillé de lancer plutôt une nouvelle exception en utilisant `throw(e)`. Dans Julia 1.1 et versions ultérieures, l'utilisation de `throw(e)` préservera l'exception de cause racine sur la pile, comme décrit dans [`current_exceptions`](@ref).

