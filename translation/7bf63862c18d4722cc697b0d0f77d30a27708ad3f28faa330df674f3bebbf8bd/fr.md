```
(::Type{T})(te::GitTreeEntry) where T<:GitObject
```

Obtenez l'objet git auquel `te` fait référence et renvoyez-le sous son type réel (le type [`entrytype`](@ref) montrerait), par exemple un `GitBlob` ou un `GitTag`.

# Exemples

```julia
tree = LibGit2.GitTree(repo, "HEAD^{tree}")
tree_entry = tree[1]
blob = LibGit2.GitBlob(tree_entry)
```
