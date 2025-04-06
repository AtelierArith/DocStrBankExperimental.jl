```
LibGit2.DiffDelta
```

对一个条目的更改描述。与 [`git_diff_delta`](https://libgit2.org/libgit2/#HEAD/type/git_diff_delta) 结构匹配。

字段表示：

  * `status`: `Consts.DELTA_STATUS` 中的一个，指示文件是否已被添加/修改/删除。
  * `flags`: 表示增量和每一侧对象的标志。决定是否将文件视为二进制/文本，是否在增量的每一侧存在，以及对象 ID 是否已知为正确。
  * `similarity`: 用于指示文件是否已被重命名或复制。
  * `nfiles`: 增量中的文件数量（例如，如果增量是在子模块提交 ID 上运行的，它可能包含多个文件）。
  * `old_file`: 一个 [`DiffFile`](@ref)，包含更改前文件的信息。
  * `new_file`: 一个 [`DiffFile`](@ref)，包含更改后文件的信息。
