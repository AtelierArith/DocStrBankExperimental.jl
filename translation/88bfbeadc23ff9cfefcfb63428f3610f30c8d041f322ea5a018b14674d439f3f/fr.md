```
pointer(array [, index])
```

Obtenez l'adresse native d'un tableau ou d'une chaîne, éventuellement à un emplacement donné `index`.

Cette fonction est "non sécurisée". Faites attention à vous assurer qu'une référence Julia à `array` existe tant que ce pointeur sera utilisé. Le macro [`GC.@preserve`](@ref) doit être utilisé pour protéger l'argument `array` de la collecte des ordures dans un bloc de code donné.

Appeler [`Ref(array[, index])`](@ref Ref) est généralement préférable à cette fonction car cela garantit la validité.
