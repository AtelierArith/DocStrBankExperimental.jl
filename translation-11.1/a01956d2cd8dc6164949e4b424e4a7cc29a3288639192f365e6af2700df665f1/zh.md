```
fetchheads(repo::GitRepo) -> Vector{FetchHead}
```

返回 `repo` 的所有 fetch heads 列表，每个 fetch head 作为 [`FetchHead`](@ref) 表示，包括它们的名称、URL 和合并状态。

# 示例

```julia-repl
julia> fetch_heads = LibGit2.fetchheads(repo);

julia> fetch_heads[1].name
"refs/heads/master"

julia> fetch_heads[1].ismerge
true

julia> fetch_heads[2].name
"refs/heads/test_branch"

julia> fetch_heads[2].ismerge
false
```
