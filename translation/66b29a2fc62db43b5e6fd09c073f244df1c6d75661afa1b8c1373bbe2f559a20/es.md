```
LibGit2.count(f::Function, walker::GitRevWalker; oid::GitHash=GitHash(), by::Cint=Consts.SORT_NONE, rev::Bool=false)
```

Usando el [`GitRevWalker`](@ref) `walker` para "caminar" sobre cada commit en la historia del repositorio, encuentra el número de commits que devuelven `true` cuando se aplica `f` a ellos. Los argumentos clave son:     * `oid`: El [`GitHash`](@ref) del commit desde el cual comenzar el recorrido. El valor predeterminado es usar       [`push_head!`](@ref) y, por lo tanto, el commit HEAD y todos sus ancestros.     * `by`: El método de ordenamiento. El valor predeterminado es no ordenar. Otras opciones son ordenar por       topología (`LibGit2.Consts.SORT_TOPOLOGICAL`), ordenar hacia adelante en el tiempo       (`LibGit2.Consts.SORT_TIME`, el más antiguo primero) o ordenar hacia atrás en el tiempo       (`LibGit2.Consts.SORT_REVERSE`, el más reciente primero).     * `rev`: Si se debe invertir el orden de los resultados ordenados (por ejemplo, si se utiliza el ordenamiento topológico).

# Ejemplos

```julia
cnt = LibGit2.with(LibGit2.GitRevWalker(repo)) do walker
    LibGit2.count((oid, repo)->(oid == commit_oid1), walker, oid=commit_oid1, by=LibGit2.Consts.SORT_TIME)
end
```

`LibGit2.count` encuentra el número de commits a lo largo del recorrido con un cierto `GitHash` `commit_oid1`, comenzando el recorrido desde ese commit y avanzando en el tiempo desde él. Dado que el `GitHash` es único para un commit, `cnt` será `1`.
