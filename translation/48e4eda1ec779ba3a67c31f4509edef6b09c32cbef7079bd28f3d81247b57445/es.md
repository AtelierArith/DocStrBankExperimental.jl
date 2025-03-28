```
update!(repo::GitRepo, files::AbstractString...)
update!(idx::GitIndex, files::AbstractString...)
```

Actualiza todos los archivos con rutas especificadas por `files` en el índice `idx` (o el índice del `repo`). Coincide el estado de cada archivo en el índice con el estado actual en el disco, eliminándolo si ha sido eliminado en el disco, o actualizando su entrada en la base de datos de objetos.
