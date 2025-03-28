```
include_dependency(path::AbstractString; track_content::Bool=true)
```

Dans un module, déclarez que le fichier, le répertoire ou le lien symbolique spécifié par `path` (relatif ou absolu) est une dépendance pour la précompilation ; c'est-à-dire que si `track_content=true`, le module devra être recompilé si le contenu de `path` change (si `path` est un répertoire, le contenu équivaut à `join(readdir(path))`). Si `track_content=false`, la recompilation est déclenchée lorsque le temps de modification `mtime` de `path` change.

Cela n'est nécessaire que si votre module dépend d'un chemin qui n'est pas utilisé via [`include`](@ref). Cela n'a aucun effet en dehors de la compilation.

!!! compat "Julia 1.11"
    L'argument clé `track_content` nécessite au moins Julia 1.11. Une erreur est maintenant lancée si `path` n'est pas lisible.

