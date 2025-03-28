```
GitObject(repo::GitRepo, hash::AbstractGitHash)
GitObject(repo::GitRepo, spec::AbstractString)
```

Gibt das angegebene Objekt ([`GitCommit`](@ref), [`GitBlob`](@ref), [`GitTree`](@ref) oder [`GitTag`](@ref)) aus `repo` zurück, das durch `hash`/`spec` angegeben ist.

  * `hash` ist ein vollständiger (`GitHash`) oder teilweiser (`GitShortHash`) Hash.
  * `spec` ist eine textuelle Spezifikation: siehe [die git-Dokumentation](https://git-scm.com/docs/git-rev-parse.html#_specifying_revisions) für eine vollständige Liste.
