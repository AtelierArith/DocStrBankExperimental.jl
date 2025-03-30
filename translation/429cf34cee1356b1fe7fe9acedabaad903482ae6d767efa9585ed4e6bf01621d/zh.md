```
fetch_refspecs(rmt::GitRemote) -> Vector{String}
```

获取指定 `rmt` 的 *fetch* refspecs。这些 refspecs 包含有关要从中获取的分支的信息。

# 示例

```julia-repl
julia> remote = LibGit2.get(LibGit2.GitRemote, repo, "upstream");

julia> LibGit2.add_fetch!(repo, remote, "upstream");

julia> LibGit2.fetch_refspecs(remote)
String["+refs/heads/*:refs/remotes/upstream/*"]
```
