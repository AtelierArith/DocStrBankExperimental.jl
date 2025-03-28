```
LibGit2.init(path::AbstractString, bare::Bool=false) -> GitRepo
```

Ouvre un nouveau dépôt git à `path`. Si `bare` est `false`, l'arborescence de travail sera créée dans `path/.git`. Si `bare` est `true`, aucun répertoire de travail ne sera créé.
