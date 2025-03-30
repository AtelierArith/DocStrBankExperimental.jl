```
LibGit2.GitStatus(repo::GitRepo; status_opts=StatusOptions())
```

收集关于 git 仓库 `repo` 中每个文件状态的信息（例如，文件是否被修改、已暂存等）。`status_opts` 可用于设置各种选项，例如是否查看未跟踪的文件或是否包含子模块等。有关更多信息，请参见 [`StatusOptions`](@ref)。
