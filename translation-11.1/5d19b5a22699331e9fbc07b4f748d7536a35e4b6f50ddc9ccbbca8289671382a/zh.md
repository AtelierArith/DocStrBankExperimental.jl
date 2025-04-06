```
verify_host(url::AbstractString, [transport::AbstractString]) :: Bool
```

`verify_host` 函数告诉调用者在通过安全传输（如 TLS 或 SSH）进行通信时，是否应该验证主机的身份。`url` 参数可以是：

1. 以 `proto://` 开头的正确 URL
2. `ssh` 风格的裸主机名或以 `user@` 为前缀的主机名
3. 如上所述的 `scp` 风格的主机，后跟 `:` 和路径位置

在每种情况下，主机名部分被解析出来，是否验证的决定仅基于主机名，而不是输入 URL 的其他内容。特别是，URL 的协议并不重要（更多内容见下文）。

`transport` 参数指示查询所涉及的传输类型。目前已知的值为 `SSL`/`ssl`（别名 `TLS`/`tls`）和 `SSH`/`ssh`。如果省略 `transport`，查询将仅在主机名不应被验证时返回 `true`，而与传输无关。

主机名与相关环境变量中的主机模式进行匹配，具体取决于是否提供 `transport` 及其值：

  * `JULIA_NO_VERIFY_HOSTS` — 不应验证的主机，适用于任何传输
  * `JULIA_SSL_NO_VERIFY_HOSTS` — 不应验证的主机，适用于 SSL/TLS
  * `JULIA_SSH_NO_VERIFY_HOSTS` — 不应验证的主机，适用于 SSH
  * `JULIA_ALWAYS_VERIFY_HOSTS` — 应始终验证的主机

这些变量的值是一个以逗号分隔的主机名模式列表，具有以下语法 — 每个模式在 `.` 上拆分为部分，每部分必须是：

1. 由一个或多个 ASCII 字母、数字、连字符或下划线组成的字面域名组件（技术上不属于合法主机名的一部分，但有时使用）。字面域名组件仅匹配其自身。
2. `**`，匹配零个或多个域名组件。
3. `*`，匹配任何一个域名组件。

在将主机名与这些变量中的模式列表进行匹配时，主机名在 `.` 上拆分为组件，该单词序列与模式进行匹配：字面模式精确匹配一个具有该值的主机名组件；`*` 模式精确匹配一个具有任何值的主机名组件；`**` 模式匹配任意数量的主机名组件。例如：

  * `**` 匹配任何主机名
  * `**.org` 匹配任何在 `.org` 顶级域中的主机名
  * `example.com` 仅匹配确切的主机名 `example.com`
  * `*.example.com` 匹配 `api.example.com` 但不匹配 `example.com` 或 `v1.api.example.com`
  * `**.example.com` 匹配 `example.com` 下的任何域，包括 `example.com` 本身、`api.example.com` 和 `v1.api.example.com`

```
