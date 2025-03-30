```
LibGit2.StatusEntry
```

提供文件在 HEAD 和索引中的差异，以及索引和工作目录之间的差异。与 `git_status_entry` 结构体相匹配。

字段表示：

  * `status`：包含文件的状态标志，指示它是否是当前的，或者在索引或工作树中以某种方式发生了变化。
  * `head_to_index`：指向一个 [`DiffDelta`](@ref) 的指针，该指针封装了文件在 HEAD 和索引中存在的差异。
  * `index_to_workdir`：指向一个 `DiffDelta` 的指针，该指针封装了文件在索引和 [`workdir`](@ref) 中存在的差异。
