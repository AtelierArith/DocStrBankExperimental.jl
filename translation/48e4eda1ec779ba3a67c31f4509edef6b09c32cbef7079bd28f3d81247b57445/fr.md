```
update!(repo::GitRepo, files::AbstractString...)
update!(idx::GitIndex, files::AbstractString...)
```

Met à jour tous les fichiers dont les chemins sont spécifiés par `files` dans l'index `idx` (ou l'index du `repo`). Fait correspondre l'état de chaque fichier dans l'index avec l'état actuel sur le disque, en le supprimant s'il a été supprimé sur le disque, ou en mettant à jour son entrée dans la base de données d'objets.
