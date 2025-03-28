```
lookup_branch(repo::GitRepo, branch_name::AbstractString, remote::Bool=false) -> Union{GitReference, Nothing}
```

Déterminez si la branche spécifiée par `branch_name` existe dans le dépôt `repo`. Si `remote` est `true`, `repo` est supposé être un dépôt git distant. Sinon, il fait partie du système de fichiers local.

Retournez soit une `GitReference` vers la branche demandée si elle existe, soit [`nothing`](@ref) si ce n'est pas le cas.
