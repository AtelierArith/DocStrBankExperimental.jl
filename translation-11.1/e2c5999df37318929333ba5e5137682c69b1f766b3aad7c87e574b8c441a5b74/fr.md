```
isreadable(path::String)
```

Retourne `true` si les permissions d'accès pour le `path` donné permettent la lecture par l'utilisateur actuel.

!!! note
    Cette permission peut changer avant que l'utilisateur n'appelle `open`, il est donc recommandé d'appeler simplement `open` seul et de gérer l'erreur si cela échoue, plutôt que d'appeler `isreadable` en premier.


!!! note
    Actuellement, cette fonction n'interroge pas correctement les ACL du système de fichiers sur Windows, elle peut donc renvoyer des résultats incorrects.


!!! compat "Julia 1.11"
    Cette fonction nécessite au moins Julia 1.11.


Voir aussi [`ispath`](@ref), [`isexecutable`](@ref), [`iswritable`](@ref).
