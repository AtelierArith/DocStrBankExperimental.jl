```
LibGit2.gitdir(repo::GitRepo)
```

返回 `repo` 的 "git" 文件的位置：

  * 对于普通仓库，这是 `.git` 文件夹的位置。
  * 对于裸仓库，这是仓库本身的位置。

另见 [`workdir`](@ref), [`path`](@ref).
