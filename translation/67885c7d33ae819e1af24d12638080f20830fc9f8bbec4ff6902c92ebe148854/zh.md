```
LibGit2.DescribeFormatOptions
```

匹配 [`git_describe_format_options`](https://libgit2.org/libgit2/#HEAD/type/git_describe_format_options) 结构体。

字段表示：

  * `version`: 正在使用的结构体版本，以防将来更改。目前始终为 `1`。
  * `abbreviated_size`: 要使用的简化 `GitHash` 的下限大小，默认为 `7`。
  * `always_use_long_format`: 设置为 `1` 以在可以使用短格式的情况下仍然使用长格式字符串。
  * `dirty_suffix`: 如果设置，将在描述字符串的末尾附加此内容，如果 [`workdir`](@ref) 是脏的。
