```
LibGit2.map(f::Function, walker::GitRevWalker; oid::GitHash=GitHash(), range::AbstractString="", by::Cint=Consts.SORT_NONE, rev::Bool=false)
```

Usando el [`GitRevWalker`](@ref) `walker` para "caminar" sobre cada commit en la historia del repositorio, aplica `f` a cada commit en el recorrido. Los argumentos clave son:     * `oid`: El [`GitHash`](@ref) del commit desde el cual comenzar el recorrido. El valor predeterminado es usar       [`push_head!`](@ref) y, por lo tanto, el commit HEAD y todos sus ancestros.     * `range`: Un rango de `GitHash`s en el formato `oid1..oid2`. `f` se aplicará a todos los commits entre los dos.     * `by`: El método de ordenamiento. El valor predeterminado es no ordenar. Otras opciones son ordenar por       topología (`LibGit2.Consts.SORT_TOPOLOGICAL`), ordenar hacia adelante en el tiempo       (`LibGit2.Consts.SORT_TIME`, el más antiguo primero) o ordenar hacia atrás en el tiempo       (`LibGit2.Consts.SORT_REVERSE`, el más reciente primero).     * `rev`: Si se debe invertir el orden ordenado (por ejemplo, si se utiliza el ordenamiento topológico).

# Ejemplos

```julia
oids = LibGit2.with(LibGit2.GitRevWalker(repo)) do walker
    LibGit2.map((oid, repo)->string(oid), walker, by=LibGit2.Consts.SORT_TIME)
end
```

Aquí, `LibGit2.map` visita cada commit usando el `GitRevWalker` y encuentra su `GitHash`.
