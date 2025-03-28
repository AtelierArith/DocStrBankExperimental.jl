```
GitRevWalker(repo::GitRepo)
```

Ein `GitRevWalker` *geht* durch die *Revisionen* (d.h. Commits) eines Git-Repositorys `repo`. Es ist eine Sammlung der Commits im Repository und unterstützt Iteration sowie Aufrufe von [`LibGit2.map`](@ref) und [`LibGit2.count`](@ref) (zum Beispiel könnte `LibGit2.count` verwendet werden, um zu bestimmen, welcher Prozentsatz der Commits in einem Repository von einem bestimmten Autor erstellt wurde).

```julia
cnt = LibGit2.with(LibGit2.GitRevWalker(repo)) do walker
    LibGit2.count((oid,repo)->(oid == commit_oid1), walker, oid=commit_oid1, by=LibGit2.Consts.SORT_TIME)
end
```

Hier findet `LibGit2.count` die Anzahl der Commits entlang des Weges mit einem bestimmten `GitHash`. Da der `GitHash` einzigartig für einen Commit ist, wird `cnt` `1` sein.
