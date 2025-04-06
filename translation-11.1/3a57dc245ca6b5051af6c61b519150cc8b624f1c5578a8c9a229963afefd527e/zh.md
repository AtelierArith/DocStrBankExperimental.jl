```
transact(f::Function, repo::GitRepo)
```

将函数 `f` 应用到 git 仓库 `repo`，在应用 `f` 之前先进行 [`snapshot`](@ref)。如果在 `f` 内部发生错误，`repo` 将使用 [`restore`](@ref) 返回到其快照状态。发生的错误将被重新抛出，但 `repo` 的状态不会被损坏。
