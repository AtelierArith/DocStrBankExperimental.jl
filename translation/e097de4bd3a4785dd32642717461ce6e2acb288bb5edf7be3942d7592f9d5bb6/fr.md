```
LibGit2.create_branch(repo::GitRepo, bname::AbstractString, commit_obj::GitCommit; force::Bool=false)
```

Crée une nouvelle branche dans le dépôt `repo` avec le nom `bname`, qui pointe vers le commit `commit_obj` (qui doit faire partie de `repo`). Si `force` est `true`, écrase une branche existante nommée `bname` si elle existe. Si `force` est `false` et qu'une branche existe déjà nommée `bname`, cette fonction lancera une erreur.
