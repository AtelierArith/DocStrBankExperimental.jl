```
LibGit2.create_branch(repo::GitRepo, bname::AbstractString, commit_obj::GitCommit; force::Bool=false)
```

Erstellt einen neuen Branch im Repository `repo` mit dem Namen `bname`, der auf den Commit `commit_obj` zeigt (der Teil von `repo` sein muss). Wenn `force` `true` ist, wird ein vorhandener Branch mit dem Namen `bname` überschrieben, falls er existiert. Wenn `force` `false` ist und bereits ein Branch mit dem Namen `bname` existiert, wird diese Funktion einen Fehler auslösen.
