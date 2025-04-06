```
restore(s::State, repo::GitRepo)
```

将仓库 `repo` 恢复到之前的 `State` `s`，例如在合并尝试之前的分支的 HEAD。`s` 可以使用 [`snapshot`](@ref) 函数生成。
