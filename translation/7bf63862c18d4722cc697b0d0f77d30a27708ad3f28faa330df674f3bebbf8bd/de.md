```
(::Type{T})(te::GitTreeEntry) where T<:GitObject
```

Holen Sie das Git-Objekt, auf das `te` verweist, und geben Sie es als seinen tatsächlichen Typ zurück (der Typ [`entrytype`](@ref) würde angezeigt), zum Beispiel ein `GitBlob` oder `GitTag`.

# Beispiele

```julia
tree = LibGit2.GitTree(repo, "HEAD^{tree}")
tree_entry = tree[1]
blob = LibGit2.GitBlob(tree_entry)
```
