```
(::Type{T})(te::GitTreeEntry) where T<:GitObject
```

`te`'ye atıfta bulunan git nesnesini al ve onu gerçek türü olarak döndür (örneğin [`entrytype`](@ref) türü gösterir), örneğin bir `GitBlob` veya `GitTag`.

# Örnekler

```julia
tree = LibGit2.GitTree(repo, "HEAD^{tree}")
tree_entry = tree[1]
blob = LibGit2.GitBlob(tree_entry)
```
