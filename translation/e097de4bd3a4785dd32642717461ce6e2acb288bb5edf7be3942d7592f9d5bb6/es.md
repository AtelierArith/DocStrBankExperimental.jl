```
LibGit2.create_branch(repo::GitRepo, bname::AbstractString, commit_obj::GitCommit; force::Bool=false)
```

Crea una nueva rama en el repositorio `repo` con el nombre `bname`, que apunta al commit `commit_obj` (que debe ser parte de `repo`). Si `force` es `true`, sobrescribe una rama existente llamada `bname` si existe. Si `force` es `false` y ya existe una rama llamada `bname`, esta función lanzará un error.
