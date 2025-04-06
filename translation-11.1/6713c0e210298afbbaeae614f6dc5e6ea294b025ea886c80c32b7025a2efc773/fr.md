```
remove!(repo::GitRepo, files::AbstractString...)
remove!(idx::GitIndex, files::AbstractString...)
```

Supprime tous les fichiers dont les chemins sont spécifiés par `files` dans l'index `idx` (ou l'index du `repo`).
