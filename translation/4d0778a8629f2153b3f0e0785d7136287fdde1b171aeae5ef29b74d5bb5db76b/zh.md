```
GitTree(repo::GitRepo, hash::AbstractGitHash)
GitTree(repo::GitRepo, spec::AbstractString)
```

从由 `hash`/`spec` 指定的 `repo` 返回一个 `GitTree` 对象。

  * `hash` 是一个完整的 (`GitHash`) 或部分的 (`GitShortHash`) 哈希。
  * `spec` 是一个文本规范：请参见 [the git docs](https://git-scm.com/docs/git-rev-parse.html#_specifying_revisions) 获取完整列表。
