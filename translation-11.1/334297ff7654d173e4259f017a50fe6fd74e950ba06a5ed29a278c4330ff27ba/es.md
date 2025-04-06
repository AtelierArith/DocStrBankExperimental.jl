```
LibGit2.path(repo::GitRepo)
```

Devuelve la ruta base del archivo del repositorio `repo`.

  * para repositorios normales, esto será típicamente el directorio padre del directorio ".git" (nota: esto puede ser diferente del directorio de trabajo, consulta `workdir` para más detalles).
  * para repositorios bare, esta es la ubicación de los archivos "git".

Consulta también [`gitdir`](@ref), [`workdir`](@ref).
