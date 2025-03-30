```
LibGit2.read_tree!(idx::GitIndex, tree::GitTree)
LibGit2.read_tree!(idx::GitIndex, treehash::AbstractGitHash)
```

将树 `tree`（或由 `treehash` 指向的树，在 `idx` 所拥有的仓库中）读取到索引 `idx` 中。当前的索引内容将被替换。
