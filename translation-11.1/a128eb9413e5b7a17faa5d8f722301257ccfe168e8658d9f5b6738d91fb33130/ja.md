```
add_push!(repo::GitRepo, rmt::GitRemote, push_spec::String)
```

指定された `rmt` のために *push* refspec を追加します。この refspec には、どのブランチをプッシュするかに関する情報が含まれます。

# 例

```julia-repl
julia> LibGit2.add_push!(repo, remote, "refs/heads/master");

julia> remote = LibGit2.get(LibGit2.GitRemote, repo, branch);

julia> LibGit2.push_refspecs(remote)
String["refs/heads/master"]
```

!!! note
    プッシュ refspecs を更新した後、変更を有効にし、[`push`](@ref) の呼び出しが機能するためには、対象の `GitRemote` を [`close`](@ref) して再度開く必要があるかもしれません。

