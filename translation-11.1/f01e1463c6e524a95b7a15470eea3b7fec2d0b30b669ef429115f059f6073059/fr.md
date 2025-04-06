```
LibGit2.status(repo::GitRepo, path::String) -> Union{Cuint, Cvoid}
```

Vérifiez le statut du fichier à `path` dans le dépôt git `repo`. Par exemple, cela peut être utilisé pour vérifier si le fichier à `path` a été modifié et doit être mis en scène et engagé.
