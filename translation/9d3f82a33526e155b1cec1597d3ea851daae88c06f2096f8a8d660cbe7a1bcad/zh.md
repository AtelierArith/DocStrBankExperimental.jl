```
snapshot(repo::GitRepo) -> State
```

获取当前仓库 `repo` 的快照，存储当前的 HEAD、索引和任何未提交的工作。输出的 `State` 可以在后续调用 [`restore`](@ref) 时使用，以将仓库恢复到快照状态。
