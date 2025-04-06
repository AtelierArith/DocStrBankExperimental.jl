```
readavailable(stream)
```

Lire les données mises en mémoire tampon disponibles à partir d'un flux. Les opérations d'E/S réelles ne sont effectuées que si aucune donnée n'a déjà été mise en mémoire tampon. Le résultat est un `Vector{UInt8}`.

!!! warning
    La quantité de données renvoyées dépend de l'implémentation ; par exemple, elle peut dépendre du choix interne de la taille du tampon. D'autres fonctions telles que [`read`](@ref) devraient généralement être utilisées à la place.

