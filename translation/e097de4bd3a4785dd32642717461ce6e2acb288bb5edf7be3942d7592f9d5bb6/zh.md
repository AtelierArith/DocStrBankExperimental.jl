```
LibGit2.create_branch(repo::GitRepo, bname::AbstractString, commit_obj::GitCommit; force::Bool=false)
```

在仓库 `repo` 中创建一个名为 `bname` 的新分支，该分支指向提交 `commit_obj`（该提交必须是 `repo` 的一部分）。如果 `force` 为 `true`，则如果存在名为 `bname` 的现有分支，将其覆盖。如果 `force` 为 `false` 且已存在名为 `bname` 的分支，则此函数将抛出错误。
