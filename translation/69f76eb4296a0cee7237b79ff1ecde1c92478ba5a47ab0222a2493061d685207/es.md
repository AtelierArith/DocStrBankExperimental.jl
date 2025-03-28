```
GitRevWalker(repo::GitRepo)
```

Un `GitRevWalker` *camina* a través de las *revisiones* (es decir, commits) de un repositorio git `repo`. Es una colección de los commits en el repositorio, y soporta iteración y llamadas a [`LibGit2.map`](@ref) y [`LibGit2.count`](@ref) (por ejemplo, `LibGit2.count` podría usarse para determinar qué porcentaje de commits en un repositorio fueron realizados por un cierto autor).

```julia
cnt = LibGit2.with(LibGit2.GitRevWalker(repo)) do walker
    LibGit2.count((oid,repo)->(oid == commit_oid1), walker, oid=commit_oid1, by=LibGit2.Consts.SORT_TIME)
end
```

Aquí, `LibGit2.count` encuentra el número de commits a lo largo del recorrido con un cierto `GitHash`. Dado que el `GitHash` es único para un commit, `cnt` será `1`.
