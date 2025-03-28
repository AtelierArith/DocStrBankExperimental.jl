```
GitBlob(repo::GitRepo, hash::AbstractGitHash)
GitBlob(repo::GitRepo, spec::AbstractString)
```

Gibt ein `GitBlob`-Objekt aus `repo` zurück, das durch `hash`/`spec` angegeben ist.

  * `hash` ist ein vollständiger (`GitHash`) oder teilweiser (`GitShortHash`) Hash.
  * `spec` ist eine textuelle Spezifikation: siehe [die git-Dokumentation](https://git-scm.com/docs/git-rev-parse.html#_specifying_revisions) für eine vollständige Liste.
