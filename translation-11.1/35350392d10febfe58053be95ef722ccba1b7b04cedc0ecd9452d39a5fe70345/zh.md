```
LibGit2.CheckoutOptions
```

匹配 [`git_checkout_options`](https://libgit2.org/libgit2/#HEAD/type/git_checkout_options) 结构体。

字段表示：

  * `version`: 正在使用的结构体版本，以防将来更改。目前始终为 `1`。
  * `checkout_strategy`: 确定如何处理冲突以及是否强制检出/重新创建缺失的文件。
  * `disable_filters`: 如果非零，则不应用像 CLRF 这样的过滤器（用于在 UNIX 和 DOS 之间转换文件换行符）。
  * `dir_mode`: 参与检出的任何目录的读/写/访问模式。默认值为 `0755`。
  * `file_mode`: 参与检出的任何文件的读/写/访问模式。默认值为 `0755` 或 `0644`，具体取决于 blob。
  * `file_open_flags`: 在检出期间用于打开任何文件的位标志。
  * `notify_flags`: 用户应被通知的冲突类型的标志。
  * `notify_cb`: 可选的回调函数，用于在发生检出冲突时通知用户。如果此函数返回非零值，则检出将被取消。
  * `notify_payload`: 通知回调函数的有效负载。
  * `progress_cb`: 可选的回调函数，用于显示检出进度。
  * `progress_payload`: 进度回调的有效负载。
  * `paths`: 如果不为空，描述在检出期间要搜索的路径。如果为空，检出将发生在存储库中的所有文件上。
  * `baseline`: [`workdir`](@ref) 的预期内容，捕获在（指向）[`GitTree`](@ref) 中。默认为 HEAD 时树的状态。
  * `baseline_index`: [`workdir`](@ref) 的预期内容，捕获在（指向）`GitIndex` 中。默认为 HEAD 时索引的状态。
  * `target_directory`: 如果不为空，则检出到此目录而不是 `workdir`。
  * `ancestor_label`: 在发生冲突时，公共祖先方的名称。
  * `our_label`: 在发生冲突时，“我们”一方的名称。
  * `their_label`: 在发生冲突时，“他们”一方的名称。
  * `perfdata_cb`: 可选的回调函数，用于显示性能数据。
  * `perfdata_payload`: 性能回调的有效负载。
