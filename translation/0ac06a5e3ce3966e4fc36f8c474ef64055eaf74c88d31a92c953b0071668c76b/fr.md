```
mkfifo(path::AbstractString, [mode::Integer]) -> path
```

Créer un fichier spécial FIFO (un tube nommé) à `path`. Retourner `path` tel quel en cas de succès.

`mkfifo` n'est pris en charge que sur les plateformes Unix.

!!! compat "Julia 1.11"
    `mkfifo` nécessite au moins Julia 1.11.

