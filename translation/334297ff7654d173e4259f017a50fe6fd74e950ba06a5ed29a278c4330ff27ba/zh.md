```
LibGit2.path(repo::GitRepo)
```

返回仓库 `repo` 的基本文件路径。

  * 对于普通仓库，这通常是 ".git" 目录的父目录（注意：这可能与工作目录不同，详见 `workdir`）。
  * 对于裸仓库，这是 "git" 文件的位置。

另见 [`gitdir`](@ref), [`workdir`](@ref)。
