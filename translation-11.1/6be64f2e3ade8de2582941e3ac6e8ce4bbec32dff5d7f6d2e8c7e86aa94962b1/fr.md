```
lstat(fichier)
```

Comme [`stat`](@ref), mais pour les liens symboliques, obtient les informations pour le lien lui-même plutôt que pour le fichier auquel il fait référence. Cette fonction doit être appelée sur un chemin de fichier plutôt que sur un objet fichier ou un descripteur de fichier.
