```
LibGit2.DiffFile
```

描述增量的一侧。与 [`git_diff_file`](https://libgit2.org/libgit2/#HEAD/type/git_diff_file) 结构匹配。

字段表示：

  * `id`：增量中项目的 [`GitHash`](@ref)。如果该项目在增量的这一侧为空（例如，如果增量是文件的删除），则该值为 `GitHash(0)`。
  * `path`：相对于存储库工作目录的以 `NULL` 结尾的项目路径。
  * `size`：项目的字节大小。
  * `flags`：[`git_diff_flag_t`](https://libgit2.org/libgit2/#HEAD/type/git_diff_flag_t) 标志的组合。该整数的第 `i` 位设置第 `i` 个标志。
  * `mode`：项目的 [`stat`](@ref) 模式。
  * `id_abbrev`：仅在版本大于或等于 `0.25.0` 的 LibGit2 中存在。使用 [`string`](@ref) 转换时 `id` 字段的长度。通常等于 `OID_HEXSZ`（40）。
