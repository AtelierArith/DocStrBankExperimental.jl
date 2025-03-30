```
LibGit2.StatusOptions
```

用于控制 `git_status_foreach_ext()` 如何发出回调的选项。与 [`git_status_opt_t`](https://libgit2.org/libgit2/#HEAD/type/git_status_opt_t) 结构匹配。

字段表示：

  * `version`：正在使用的结构版本，以防将来更改。目前始终为 `1`。
  * `show`：用于检查哪些文件及其顺序的标志。默认值为 `Consts.STATUS_SHOW_INDEX_AND_WORKDIR`。
  * `flags`：用于控制状态调用中使用的任何回调的标志。
  * `pathspec`：用于路径匹配的路径数组。路径匹配的行为将根据 `show` 和 `flags` 的值而有所不同。
  * `baseline` 是用于与工作目录和索引进行比较的树；默认为 HEAD。
