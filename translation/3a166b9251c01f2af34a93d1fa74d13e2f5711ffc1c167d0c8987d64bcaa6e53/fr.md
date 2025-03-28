```
edit(path::AbstractString, line::Integer=0, column::Integer=0)
```

Modifiez un fichier ou un répertoire en fournissant éventuellement un numéro de ligne pour modifier le fichier à cet endroit. Retournez à l'invite `julia` lorsque vous quittez l'éditeur. L'éditeur peut être changé en définissant `JULIA_EDITOR`, `VISUAL` ou `EDITOR` en tant que variable d'environnement.

!!! compat "Julia 1.9"
    L'argument `column` nécessite au moins Julia 1.9.


Voir aussi [`InteractiveUtils.define_editor`](@ref).
