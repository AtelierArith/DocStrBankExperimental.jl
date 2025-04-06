```
(::Type{T})(te::GitTreeEntry) where T<:GitObject
```

`te`가 참조하는 git 객체를 가져와서 그것의 실제 타입(예: [`entrytype`](@ref)에서 보여줄 타입)으로 반환합니다. 예를 들어 `GitBlob` 또는 `GitTag`가 될 수 있습니다.

# 예시

```julia
tree = LibGit2.GitTree(repo, "HEAD^{tree}")
tree_entry = tree[1]
blob = LibGit2.GitBlob(tree_entry)
```
