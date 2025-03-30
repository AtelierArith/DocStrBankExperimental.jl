```
GitRevWalker(repo::GitRepo)
```

`GitRevWalker` *遍历* git 仓库 `repo` 的 *修订*（即提交）。它是仓库中提交的集合，支持迭代和对 [`LibGit2.map`](@ref) 和 [`LibGit2.count`](@ref) 的调用（例如，`LibGit2.count` 可用于确定某个作者在仓库中提交的百分比）。

```julia
cnt = LibGit2.with(LibGit2.GitRevWalker(repo)) do walker
    LibGit2.count((oid,repo)->(oid == commit_oid1), walker, oid=commit_oid1, by=LibGit2.Consts.SORT_TIME)
end
```

在这里，`LibGit2.count` 找到沿着遍历与某个 `GitHash` 相关的提交数量。由于 `GitHash` 是提交的唯一标识，`cnt` 将为 `1`。
