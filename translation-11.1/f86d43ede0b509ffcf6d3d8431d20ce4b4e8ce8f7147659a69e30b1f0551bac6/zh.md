```
push_refspecs(rmt::GitRemote) -> Vector{String}
```

获取指定 `rmt` 的 *push* refspecs。这些 refspecs 包含有关要推送到哪些分支的信息。

# 示例

```julia-repl
julia> remote = LibGit2.get(LibGit2.GitRemote, repo, "upstream");

julia> LibGit2.add_push!(repo, remote, "refs/heads/master");

julia> close(remote);

julia> remote = LibGit2.get(LibGit2.GitRemote, repo, "upstream");

julia> LibGit2.push_refspecs(remote)
String["refs/heads/master"]
```
