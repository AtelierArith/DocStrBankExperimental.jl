```
LibGit2.BlameOptions
```

匹配 [`git_blame_options`](https://libgit2.org/libgit2/#HEAD/type/git_blame_options) 结构体。

字段表示：

  * `version`：正在使用的结构体版本，以防将来更改。目前始终为 `1`。
  * `flags`：`Consts.BLAME_NORMAL` 或 `Consts.BLAME_FIRST_PARENT` 之一（libgit2 尚未实现其他 blame 标志）。
  * `min_match_characters`：在提交中必须更改的最小 *字母数字* 字符数，以便将更改与该提交关联。默认值为 20。仅在使用 `Consts.BLAME_*_COPIES` 标志之一时生效，而 libgit2 尚未实现这些标志。
  * `newest_commit`：要查看更改的最新提交的 [`GitHash`](@ref)。
  * `oldest_commit`：要查看更改的最旧提交的 [`GitHash`](@ref)。
  * `min_line`：开始 blame 的文件的第一行。默认值为 `1`。
  * `max_line`：要 blame 的文件的最后一行。默认值为 `0`，表示文件的最后一行。
