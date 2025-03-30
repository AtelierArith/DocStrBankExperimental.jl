```
remove!(repo::GitRepo, files::AbstractString...)
remove!(idx::GitIndex, files::AbstractString...)
```

从索引 `idx`（或 `repo` 的索引）中删除由 `files` 指定路径的所有文件。
