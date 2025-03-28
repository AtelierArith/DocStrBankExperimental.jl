```
LibGit2.status(repo::GitRepo, path::String) -> Union{Cuint, Cvoid}
```

Consulta el estado del archivo en `path` en el repositorio git `repo`. Por ejemplo, esto se puede usar para verificar si el archivo en `path` ha sido modificado y necesita ser preparado y confirmado.
