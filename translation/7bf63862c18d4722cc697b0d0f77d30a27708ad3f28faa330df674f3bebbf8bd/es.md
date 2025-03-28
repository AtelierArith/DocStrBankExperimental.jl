```
(::Type{T})(te::GitTreeEntry) where T<:GitObject
```

Obtiene el objeto git al que se refiere `te` y lo devuelve como su tipo real (el tipo [`entrytype`](@ref) mostraría), por ejemplo, un `GitBlob` o `GitTag`.

# Ejemplos

```julia
tree = LibGit2.GitTree(repo, "HEAD^{tree}")
tree_entry = tree[1]
blob = LibGit2.GitBlob(tree_entry)
```
