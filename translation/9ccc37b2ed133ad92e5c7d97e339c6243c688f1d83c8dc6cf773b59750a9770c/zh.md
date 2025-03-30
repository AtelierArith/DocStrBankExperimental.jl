```
GitObject(repo::GitRepo, hash::AbstractGitHash)
GitObject(repo::GitRepo, spec::AbstractString)
```

从 `repo` 中返回由 `hash`/`spec` 指定的对象（[`GitCommit`](@ref), [`GitBlob`](@ref), [`GitTree`](@ref) 或 [`GitTag`](@ref)）。

  * `hash` 是完整的 (`GitHash`) 或部分的 (`GitShortHash`) 哈希。
  * `spec` 是文本规范：请参见 [the git docs](https://git-scm.com/docs/git-rev-parse.html#_specifying_revisions) 获取完整列表。
