```
(::Type{T})(te::GitTreeEntry) where T<:GitObject
```

获取 `te` 所指的 git 对象，并将其作为实际类型返回（例如 [`entrytype`](@ref) 将显示的类型），例如 `GitBlob` 或 `GitTag`。

# 示例

```julia
tree = LibGit2.GitTree(repo, "HEAD^{tree}")
tree_entry = tree[1]
blob = LibGit2.GitBlob(tree_entry)
```
