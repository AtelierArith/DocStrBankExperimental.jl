```
LibGit2.init(path::AbstractString, bare::Bool=false) -> GitRepo
```

在 `path` 处打开一个新的 git 仓库。如果 `bare` 为 `false`，工作树将被创建在 `path/.git` 中。如果 `bare` 为 `true`，则不会创建工作目录。
