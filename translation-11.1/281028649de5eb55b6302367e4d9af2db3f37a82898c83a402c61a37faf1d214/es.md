```
GitCommit(repo::GitRepo, hash::AbstractGitHash)
GitCommit(repo::GitRepo, spec::AbstractString)
```

Devuelve un objeto `GitCommit` de `repo` especificado por `hash`/`spec`.

  * `hash` es un hash completo (`GitHash`) o parcial (`GitShortHash`).
  * `spec` es una especificación textual: consulta [la documentación de git](https://git-scm.com/docs/git-rev-parse.html#_specifying_revisions) para una lista completa.
