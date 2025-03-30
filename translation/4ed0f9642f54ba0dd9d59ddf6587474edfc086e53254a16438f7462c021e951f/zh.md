```
LibGit2.workdir(repo::GitRepo)
```

返回 `repo` 的工作目录位置。这对于裸仓库会抛出错误。

!!! note
    这通常是 `gitdir(repo)` 的父目录，但在某些情况下可能会不同：例如，如果设置了 `core.worktree` 配置变量或 `GIT_WORK_TREE` 环境变量。


另请参见 [`gitdir`](@ref), [`path`](@ref).
