```
Module
```

Un `Module` est un espace de travail de variables globales séparé. Voir [`module`](@ref) et la [section du manuel sur les modules](@ref modules) pour plus de détails.

```
Module(name::Symbol=:anonymous, std_imports=true, default_names=true)
```

Retourne un module avec le nom spécifié. Un `baremodule` correspond à `Module(:ModuleName, false)`

Un module vide ne contenant aucun nom peut être créé avec `Module(:ModuleName, false, false)`. Ce module n'importera ni `Base` ni `Core` et ne contient pas de référence à lui-même.
