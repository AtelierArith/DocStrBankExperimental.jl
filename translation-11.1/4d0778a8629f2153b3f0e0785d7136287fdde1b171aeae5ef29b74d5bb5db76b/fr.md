```
GitTree(repo::GitRepo, hash::AbstractGitHash)
GitTree(repo::GitRepo, spec::AbstractString)
```

Retourne un objet `GitTree` de `repo` spécifié par `hash`/`spec`.

  * `hash` est un hash complet (`GitHash`) ou partiel (`GitShortHash`).
  * `spec` est une spécification textuelle : voir [les docs git](https://git-scm.com/docs/git-rev-parse.html#_specifying_revisions) pour une liste complète.
