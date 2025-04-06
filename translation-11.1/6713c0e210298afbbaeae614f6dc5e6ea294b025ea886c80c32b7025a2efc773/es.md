```
remove!(repo::GitRepo, files::AbstractString...)
remove!(idx::GitIndex, files::AbstractString...)
```

Elimina todos los archivos con rutas especificadas por `files` en el índice `idx` (o el índice del `repo`).
