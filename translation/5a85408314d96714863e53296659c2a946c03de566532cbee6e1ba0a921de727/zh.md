```
lookup_branch(repo::GitRepo, branch_name::AbstractString, remote::Bool=false) -> Union{GitReference, Nothing}
```

确定由 `branch_name` 指定的分支是否存在于仓库 `repo` 中。如果 `remote` 为 `true`，则假定 `repo` 是一个远程 git 仓库。否则，它是本地文件系统的一部分。

如果请求的分支存在，则返回一个指向该分支的 `GitReference`，如果不存在，则返回 [`nothing`](@ref)。
