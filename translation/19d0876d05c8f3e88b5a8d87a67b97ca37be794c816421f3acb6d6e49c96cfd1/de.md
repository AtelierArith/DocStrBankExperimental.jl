```
LibGit2.map(f::Function, walker::GitRevWalker; oid::GitHash=GitHash(), range::AbstractString="", by::Cint=Consts.SORT_NONE, rev::Bool=false)
```

Mit dem [`GitRevWalker`](@ref) `walker`, um über jeden Commit in der Historie des Repositories zu "gehen", wende `f` auf jeden Commit im Verlauf an. Die Schlüsselwortargumente sind:     * `oid`: Der [`GitHash`](@ref) des Commits, von dem aus der Verlauf begonnen wird. Der Standardwert ist die Verwendung von       [`push_head!`](@ref) und damit des HEAD-Commits und aller seiner Vorfahren.     * `range`: Ein Bereich von `GitHash`s im Format `oid1..oid2`. `f` wird       auf alle Commits zwischen den beiden angewendet.     * `by`: Die Sortiermethode. Der Standardwert ist, nicht zu sortieren. Weitere Optionen sind, nach       Topologie zu sortieren (`LibGit2.Consts.SORT_TOPOLOGICAL`), vorwärts in der Zeit zu sortieren       (`LibGit2.Consts.SORT_TIME`, die ältesten zuerst) oder rückwärts in der Zeit zu sortieren       (`LibGit2.Consts.SORT_REVERSE`, die aktuellsten zuerst).     * `rev`: Ob die sortierte Reihenfolge umgekehrt werden soll (zum Beispiel, wenn die topologische Sortierung verwendet wird).

# Beispiele

```julia
oids = LibGit2.with(LibGit2.GitRevWalker(repo)) do walker
    LibGit2.map((oid, repo)->string(oid), walker, by=LibGit2.Consts.SORT_TIME)
end
```

Hier besucht `LibGit2.map` jeden Commit mit dem `GitRevWalker` und findet seinen `GitHash`.
