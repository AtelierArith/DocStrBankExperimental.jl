```
GitCommit(repo::GitRepo, hash::AbstractGitHash)
GitCommit(repo::GitRepo, spec::AbstractString)
```

Retourne un objet `GitCommit` à partir de `repo` spécifié par `hash`/`spec`.

  * `hash` est un hash complet (`GitHash`) ou partiel (`GitShortHash`).
  * `spec` est une spécification textuelle : voir [la documentation git](https://git-scm.com/docs/git-rev-parse.html#_specifying_revisions) pour une liste complète.
