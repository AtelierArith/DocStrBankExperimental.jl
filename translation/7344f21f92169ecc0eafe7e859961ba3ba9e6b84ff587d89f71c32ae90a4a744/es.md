```
LibGit2.gitdir(repo::GitRepo)
```

Devuelve la ubicación de los archivos "git" de `repo`:

  * para repositorios normales, esta es la ubicación de la carpeta `.git`.
  * para repositorios bare, esta es la ubicación del propio repositorio.

Ver también [`workdir`](@ref), [`path`](@ref).
