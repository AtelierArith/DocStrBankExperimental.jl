```
LibGit2.workdir(repo::GitRepo)
```

Devuelve la ubicación del directorio de trabajo de `repo`. Esto generará un error para repositorios bare.

!!! note
    Esto será típicamente el directorio padre de `gitdir(repo)`, pero puede ser diferente en algunos casos: por ejemplo, si se establece la variable de configuración `core.worktree` o la variable de entorno `GIT_WORK_TREE`.


Véase también [`gitdir`](@ref), [`path`](@ref).
