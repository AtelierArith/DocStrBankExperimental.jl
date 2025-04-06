```
LibGit2.count(f::Function, walker::GitRevWalker; oid::GitHash=GitHash(), by::Cint=Consts.SORT_NONE, rev::Bool=false)
```

Verwenden Sie den [`GitRevWalker`](@ref) `walker`, um über jeden Commit in der Historie des Repositories zu "gehen", und finden Sie die Anzahl der Commits, die `true` zurückgeben, wenn `f` auf sie angewendet wird. Die Schlüsselwortargumente sind:     * `oid`: Der [`GitHash`](@ref) des Commits, von dem aus der Walk beginnen soll. Der Standardwert ist die Verwendung von       [`push_head!`](@ref) und damit des HEAD-Commits und aller seiner Vorfahren.     * `by`: Die Sortiermethode. Der Standardwert ist, nicht zu sortieren. Weitere Optionen sind, nach       Topologie (`LibGit2.Consts.SORT_TOPOLOGICAL`) zu sortieren, vorwärts in der Zeit       (`LibGit2.Consts.SORT_TIME`, die ältesten zuerst) oder rückwärts in der Zeit       (`LibGit2.Consts.SORT_REVERSE`, die aktuellsten zuerst) zu sortieren.     * `rev`: Ob die sortierte Reihenfolge umgekehrt werden soll (zum Beispiel, wenn die topologische Sortierung verwendet wird).

# Beispiele

```julia
cnt = LibGit2.with(LibGit2.GitRevWalker(repo)) do walker
    LibGit2.count((oid, repo)->(oid == commit_oid1), walker, oid=commit_oid1, by=LibGit2.Consts.SORT_TIME)
end
```

`LibGit2.count` findet die Anzahl der Commits entlang des Walks mit einem bestimmten `GitHash` `commit_oid1`, wobei der Walk von diesem Commit aus beginnt und vorwärts in der Zeit von ihm aus geht. Da der `GitHash` einzigartig für einen Commit ist, wird `cnt` `1` sein.
