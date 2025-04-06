```
add_fetch!(repo::GitRepo, rmt::GitRemote, fetch_spec::String)
```

为指定的 `rmt` 添加一个 *fetch* refspec。此 refspec 将包含有关要从中获取的分支的信息。

# 示例

```julia-repl
julia> LibGit2.add_fetch!(repo, remote, "upstream");

julia> LibGit2.fetch_refspecs(remote)
String["+refs/heads/*:refs/remotes/upstream/*"]
```
