```
remove!(repo::GitRepo, files::AbstractString...)
remove!(idx::GitIndex, files::AbstractString...)
```

Entferne alle Dateien mit den durch `files` angegebenen Pfaden im Index `idx` (oder im Index des `repo`).
