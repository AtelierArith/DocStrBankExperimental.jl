```
LibGit2.FetchOptions
```

匹配 [`git_fetch_options`](https://libgit2.org/libgit2/#HEAD/type/git_fetch_options) 结构体。

字段表示：

  * `version`: 正在使用的结构体版本，以防将来更改。目前始终为 `1`。
  * `callbacks`: 在获取过程中使用的远程回调。
  * `prune`: 是否在获取后执行修剪。默认使用 `GitConfig` 中的设置。
  * `update_fetchhead`: 是否在获取后更新 [`FetchHead`](@ref)。默认执行更新，这是正常的 git 行为。
  * `download_tags`: 是否下载远程存在的标签。默认请求从服务器下载的对象的标签。
  * `proxy_opts`: 通过代理连接到远程的选项。请参见 [`ProxyOptions`](@ref)。仅在 libgit2 版本大于或等于 0.25.0 时存在。
  * `custom_headers`: 获取所需的任何额外头部。仅在 libgit2 版本大于或等于 0.24.0 时存在。
