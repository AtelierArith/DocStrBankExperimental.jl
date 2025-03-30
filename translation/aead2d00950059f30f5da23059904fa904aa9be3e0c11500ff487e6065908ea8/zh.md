```
LibGit2.PushOptions
```

匹配 [`git_push_options`](https://libgit2.org/libgit2/#HEAD/type/git_push_options) 结构体。

字段表示：

  * `version`：正在使用的结构体版本，以防将来更改。目前始终为 `1`。
  * `parallelism`：如果必须创建一个包文件，则此变量设置将由包构建器生成的工作线程数量。如果为 `0`，包构建器将自动设置要使用的线程数量。默认值为 `1`。
  * `callbacks`：用于推送的回调（例如，用于与远程进行身份验证）。
  * `proxy_opts`：仅在 LibGit2 版本大于或等于 `0.25.0` 时相关。设置使用代理与远程通信的选项。有关更多信息，请参见 [`ProxyOptions`](@ref)。
  * `custom_headers`：仅在 LibGit2 版本大于或等于 `0.24.0` 时相关。推送操作所需的额外头部。
