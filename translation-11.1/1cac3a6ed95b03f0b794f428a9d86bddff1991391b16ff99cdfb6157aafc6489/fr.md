```
download(url::AbstractString, [path::AbstractString = tempname()]) -> path
```

Télécharge un fichier à partir de l'URL donnée, en le sauvegardant à l'emplacement `path`, ou si non spécifié, à un chemin temporaire. Renvoie le chemin du fichier téléchargé.

!!! note
    Depuis Julia 1.6, cette fonction est obsolète et n'est qu'un mince wrapper autour de `Downloads.download`. Dans le nouveau code, vous devriez utiliser cette fonction directement au lieu d'appeler celle-ci.

