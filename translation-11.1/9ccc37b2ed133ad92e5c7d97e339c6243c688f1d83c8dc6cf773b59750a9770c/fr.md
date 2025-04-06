```
GitObject(repo::GitRepo, hash::AbstractGitHash)
GitObject(repo::GitRepo, spec::AbstractString)
```

Retourne l'objet spécifié ([`GitCommit`](@ref), [`GitBlob`](@ref), [`GitTree`](@ref) ou [`GitTag`](@ref)) du `repo` spécifié par `hash`/`spec`.

  * `hash` est un hash complet (`GitHash`) ou partiel (`GitShortHash`).
  * `spec` est une spécification textuelle : voir [la documentation git](https://git-scm.com/docs/git-rev-parse.html#_specifying_revisions) pour une liste complète.
