```
LibGit2.gitdir(repo::GitRepo)
```

Gibt den Speicherort der "git"-Dateien von `repo` zurück:

  * für normale Repositories ist dies der Speicherort des `.git`-Ordners.
  * für bare Repositories ist dies der Speicherort des Repositories selbst.

Siehe auch [`workdir`](@ref), [`path`](@ref).
