```
add_push!(repo::GitRepo, rmt::GitRemote, push_spec::String)
```

为指定的 `rmt` 添加一个 *push* refspec。此 refspec 将包含有关要推送到哪些分支的信息。

# 示例

```julia-repl
julia> LibGit2.add_push!(repo, remote, "refs/heads/master");

julia> remote = LibGit2.get(LibGit2.GitRemote, repo, branch);

julia> LibGit2.push_refspecs(remote)
String["refs/heads/master"]
```

!!! note
    更新其推送 refspecs 后，您可能需要 [`close`](@ref) 并重新打开相关的 `GitRemote`，以使更改生效，并使对 [`push`](@ref) 的调用正常工作。

