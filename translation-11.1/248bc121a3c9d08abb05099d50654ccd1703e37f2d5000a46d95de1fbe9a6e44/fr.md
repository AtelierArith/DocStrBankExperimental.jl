```
chmod(path::AbstractString, mode::Integer; recursive::Bool=false)
```

Changez le mode de permissions de `path` à `mode`. Seuls les `mode`s entiers (par exemple `0o777`) sont actuellement pris en charge. Si `recursive=true` et que le chemin est un répertoire, toutes les permissions dans ce répertoire seront modifiées de manière récursive. Retournez `path`.

!!! note
    Avant Julia 1.6, cela ne manipulait pas correctement les ACLs du système de fichiers sur Windows, par conséquent, cela ne définissait que les bits en lecture seule sur les fichiers. Il peut maintenant manipuler les ACLs.

