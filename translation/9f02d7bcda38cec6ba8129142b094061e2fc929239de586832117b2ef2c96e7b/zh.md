```
LibGit2.GitRepoExt(path::AbstractString, flags::Cuint = Cuint(Consts.REPOSITORY_OPEN_DEFAULT))
```

在 `path` 处打开一个 git 仓库，并提供扩展控制（例如，如果当前用户必须是特殊访问组的成员才能读取 `path`）。
