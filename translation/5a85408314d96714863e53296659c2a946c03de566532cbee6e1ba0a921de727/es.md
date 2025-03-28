```
lookup_branch(repo::GitRepo, branch_name::AbstractString, remote::Bool=false) -> Union{GitReference, Nothing}
```

Determina si la rama especificada por `branch_name` existe en el repositorio `repo`. Si `remote` es `true`, se asume que `repo` es un repositorio git remoto. De lo contrario, es parte del sistema de archivos local.

Devuelve ya sea un `GitReference` a la rama solicitada si existe, o [`nothing`](@ref) si no.
