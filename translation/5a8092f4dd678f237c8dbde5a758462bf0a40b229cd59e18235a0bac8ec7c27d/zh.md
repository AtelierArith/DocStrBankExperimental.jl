```
LibGit2.MergeOptions
```

匹配 [`git_merge_options`](https://libgit2.org/libgit2/#HEAD/type/git_merge_options) 结构体。

字段表示：

  * `version`：正在使用的结构体版本，以防将来更改。目前始终为 `1`。
  * `flags`：描述合并行为的 `enum` 标志。定义在 [`git_merge_flag_t`](https://github.com/libgit2/libgit2/blob/HEAD/include/git2/merge.h#L95)。对应的 Julia 枚举是 `GIT_MERGE`，其值为：

      * `MERGE_FIND_RENAMES`：检测文件在共同祖先与“我们的”或“他们的”合并一侧之间是否被重命名。允许文件被重命名的合并。
      * `MERGE_FAIL_ON_CONFLICT`：如果发现冲突则立即退出，而不是尝试解决它。
      * `MERGE_SKIP_REUC`：在合并结果的索引上不写入 REUC 扩展。
      * `MERGE_NO_RECURSIVE`：如果要合并的提交有多个合并基础，则使用第一个，而不是尝试递归合并基础。
  * `rename_threshold`：考虑一个文件是另一个文件重命名的相似度阈值。这是一个设置相似度百分比的整数。默认值为 50。
  * `target_limit`：查找重命名时要比较的最大文件数。默认值为 200。
  * `metric`：可选的自定义函数，用于确定两个文件之间的相似度以进行重命名检测。
  * `recursion_limit`：执行合并共同祖先的合并次数的上限，以尝试为合并构建一个新的虚拟合并基础。默认值为无限制。此字段仅在 libgit2 版本高于 0.24.0 时存在。
  * `default_driver`：如果两个侧面都有更改，则使用的合并驱动程序。此字段仅在 libgit2 版本高于 0.25.0 时存在。
  * `file_favor`：如何处理 `text` 驱动程序的冲突文件内容。

      * `MERGE_FILE_FAVOR_NORMAL`：如果合并的两个侧面对某个部分都有更改，则在索引中记录冲突，`git checkout` 将使用该索引创建合并文件，用户可以参考该文件以解决冲突。这是默认值。
      * `MERGE_FILE_FAVOR_OURS`：如果合并的两个侧面对某个部分都有更改，则在索引中使用合并的“我们的”侧面的版本。
      * `MERGE_FILE_FAVOR_THEIRS`：如果合并的两个侧面对某个部分都有更改，则在索引中使用合并的“他们的”侧面的版本。
      * `MERGE_FILE_FAVOR_UNION`：如果合并的两个侧面对某个部分都有更改，则在放入索引的文件中包含来自两个侧面的每个唯一行。
  * `file_flags`：合并文件的指导方针。
