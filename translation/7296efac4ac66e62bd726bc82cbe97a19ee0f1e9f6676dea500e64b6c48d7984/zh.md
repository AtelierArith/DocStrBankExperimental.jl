```
LibGit2.DiffOptionsStruct
```

匹配 [`git_diff_options`](https://libgit2.org/libgit2/#HEAD/type/git_diff_options) 结构体。

字段表示：

  * `version`: 正在使用的结构体版本，以防将来更改。目前始终为 `1`。
  * `flags`: 控制哪些文件将出现在差异中的标志。默认为 `DIFF_NORMAL`。
  * `ignore_submodules`: 是否查看子模块中的文件。默认为 `SUBMODULE_IGNORE_UNSPECIFIED`，这意味着子模块的配置将控制它是否出现在差异中。
  * `pathspec`: 要包含在差异中的文件路径。默认是使用存储库中的所有文件。
  * `notify_cb`: 可选回调，当文件增量被添加到差异时，将通知用户差异的变化。
  * `progress_cb`: 可选回调，将显示差异进度。仅在 libgit2 版本至少为 0.24.0 时相关。
  * `payload`: 传递给 `notify_cb` 和 `progress_cb` 的有效负载。
  * `context_lines`: 用于定义一个块边缘的 *未更改* 行数。这也是在块之前/之后显示的行数，以提供上下文。默认是 3。
  * `interhunk_lines`: 允许在两个独立块之间的 *未更改* 行的最大数量，超过此数量将合并块。默认是 0。
  * `id_abbrev`: 设置要打印的缩写 [`GitHash`](@ref) 的长度。默认是 `7`。
  * `max_size`: blob 的最大文件大小。超过此大小，将被视为二进制 blob。默认是 512 MB。
  * `old_prefix`: 在差异一侧放置旧文件的虚拟文件目录。默认是 `"a"`。
  * `new_prefix`: 在差异一侧放置新文件的虚拟文件目录。默认是 `"b"`。
