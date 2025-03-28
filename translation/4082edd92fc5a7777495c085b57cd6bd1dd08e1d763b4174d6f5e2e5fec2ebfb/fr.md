```
isexecutable(path::String)
```

Retourne `true` si le `path` donné a des permissions d'exécution.

!!! note
    Cette permission peut changer avant que l'utilisateur n'exécute `path`, il est donc recommandé d'exécuter le fichier et de gérer l'erreur si cela échoue, plutôt que d'appeler `isexecutable` en premier.


!!! note
    Avant Julia 1.6, cela n'interrogeait pas correctement les ACL du système de fichiers sur Windows, par conséquent, cela retournerait `true` pour n'importe quel fichier. À partir de Julia 1.6, cela détermine correctement si le fichier est marqué comme exécutable ou non.


Voir aussi [`ispath`](@ref), [`isreadable`](@ref), [`iswritable`](@ref).
