```
LibGit2.DescribeOptions
```

匹配 [`git_describe_options`](https://libgit2.org/libgit2/#HEAD/type/git_describe_options) 结构体。

字段表示：

  * `version`: 正在使用的结构体版本，以防将来更改。目前始终为 `1`。
  * `max_candidates_tags`: 考虑在 `refs/tags` 中最近的这个数量的标签来描述一个提交。默认为 10（因此将检查最近的 10 个标签以查看它们是否描述了一个提交）。
  * `describe_strategy`: 是否考虑 `refs/tags` 中的所有条目（相当于 `git-describe --tags`）或 `refs/` 中的所有条目（相当于 `git-describe --all`）。默认情况下仅显示注释标签。如果传递 `Consts.DESCRIBE_TAGS`，将考虑所有标签，无论是否注释。如果传递 `Consts.DESCRIBE_ALL`，将考虑 `refs/` 中的任何引用。
  * `pattern`: 仅考虑与 `pattern` 匹配的标签。支持通配符扩展。
  * `only_follow_first_parent`: 在查找匹配引用与描述对象之间的距离时，仅考虑第一个父级的距离。
  * `show_commit_oid_as_fallback`: 如果找不到描述提交的匹配引用，则显示提交的 [`GitHash`](@ref) 而不是抛出错误（默认行为）。
