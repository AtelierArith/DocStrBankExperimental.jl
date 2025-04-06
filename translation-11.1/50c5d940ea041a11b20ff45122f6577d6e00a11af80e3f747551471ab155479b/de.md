```
GitAnnotated(repo::GitRepo, commit_id::GitHash)
GitAnnotated(repo::GitRepo, ref::GitReference)
GitAnnotated(repo::GitRepo, fh::FetchHead)
GitAnnotated(repo::GitRepo, committish::AbstractString)
```

Ein annotierter Git-Commit enthält Informationen darüber, wie er gefunden wurde und warum, sodass Rebase- oder Merge-Operationen mehr Informationen über den Kontext des Commits haben. Konfliktdateien enthalten Informationen über die Quell-/Zielzweige im Merge, die Konflikte aufweisen. Ein annotierter Commit kann sich beispielsweise auf die Spitze eines Remote-Zweigs beziehen, wenn ein [`FetchHead`](@ref) übergeben wird, oder auf einen Zweigkopf, der mit `GitReference` beschrieben wird.
