```
GitTag(repo::GitRepo, hash::AbstractGitHash)
GitTag(repo::GitRepo, spec::AbstractString)
```

Devuelve un objeto `GitTag` de `repo` especificado por `hash`/`spec`.

  * `hash` es un hash completo (`GitHash`) o parcial (`GitShortHash`).
  * `spec` es una especificación textual: consulta [la documentación de git](https://git-scm.com/docs/git-rev-parse.html#_specifying_revisions) para una lista completa.
