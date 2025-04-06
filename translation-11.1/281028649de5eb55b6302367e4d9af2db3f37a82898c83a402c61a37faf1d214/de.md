```
GitCommit(repo::GitRepo, hash::AbstractGitHash)
GitCommit(repo::GitRepo, spec::AbstractString)
```

Gibt ein `GitCommit`-Objekt aus `repo` zurück, das durch `hash`/`spec` angegeben ist.

  * `hash` ist ein vollständiger (`GitHash`) oder teilweiser (`GitShortHash`) Hash.
  * `spec` ist eine textuelle Spezifikation: siehe [die git-Dokumentation](https://git-scm.com/docs/git-rev-parse.html#_specifying_revisions) für eine vollständige Liste.
