```
update!(repo::GitRepo, files::AbstractString...)
update!(idx::GitIndex, files::AbstractString...)
```

更新索引 `idx`（或 `repo` 的索引）中由 `files` 指定路径的所有文件。将索引中每个文件的状态与磁盘上的当前状态进行匹配，如果文件在磁盘上已被删除，则将其移除，或者更新其在对象数据库中的条目。
