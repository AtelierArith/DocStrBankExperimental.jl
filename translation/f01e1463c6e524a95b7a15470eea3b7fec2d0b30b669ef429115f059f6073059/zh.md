```
LibGit2.status(repo::GitRepo, path::String) -> Union{Cuint, Cvoid}
```

查找 git 仓库 `repo` 中 `path` 处文件的状态。例如，这可以用来检查 `path` 处的文件是否已被修改并需要暂存和提交。
