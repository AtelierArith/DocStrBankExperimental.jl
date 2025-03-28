```
cp(src::AbstractString, dst::AbstractString; force::Bool=false, follow_symlinks::Bool=false)
```

Copie le fichier, le lien ou le répertoire de `src` vers `dst`. `force=true` supprimera d'abord un `dst` existant.

Si `follow_symlinks=false`, et que `src` est un lien symbolique, `dst` sera créé en tant que lien symbolique. Si `follow_symlinks=true` et que `src` est un lien symbolique, `dst` sera une copie du fichier ou du répertoire auquel `src` fait référence. Retourne `dst`.

!!! note
    La fonction `cp` est différente de la commande `cp`. La fonction `cp` fonctionne toujours sur l'hypothèse que `dst` est un fichier, tandis que la commande fait des choses différentes selon que `dst` est un répertoire ou un fichier. Utiliser `force=true` lorsque `dst` est un répertoire entraînera la perte de tout le contenu présent dans le répertoire `dst`, et `dst` deviendra un fichier contenant le contenu de `src` à la place.

