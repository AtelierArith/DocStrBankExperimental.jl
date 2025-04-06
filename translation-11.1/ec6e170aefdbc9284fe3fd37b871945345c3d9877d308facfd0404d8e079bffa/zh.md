```
LibGit2.ProxyOptions
```

通过代理连接的选项。

与 [`git_proxy_options`](https://libgit2.org/libgit2/#HEAD/type/git_proxy_options) 结构匹配。

字段表示：

  * `version`: 正在使用的结构版本，以防将来更改。目前始终为 `1`。
  * `proxytype`: 用于指定代理类型的 `enum`。在 [`git_proxy_t`](https://libgit2.org/libgit2/#HEAD/type/git_proxy_t) 中定义。相应的 Julia 枚举是 `GIT_PROXY`，其值为：

      * `PROXY_NONE`: 不尝试通过代理进行连接。
      * `PROXY_AUTO`: 尝试从 git 配置中找出代理配置。
      * `PROXY_SPECIFIED`: 使用此结构的 `url` 字段中给定的 URL 进行连接。

    默认是自动检测代理类型。
  * `url`: 代理的 URL。
  * `credential_cb`: 指向回调函数的指针，如果远程需要身份验证以进行连接，则会调用该函数。
  * `certificate_cb`: 指向回调函数的指针，如果证书验证失败，则会调用该函数。这让用户决定是否继续连接。如果函数返回 `1`，则允许连接。如果返回 `0`，则不允许连接。可以使用负值返回错误。
  * `payload`: 提供给两个回调函数的有效负载。

# 示例

```julia-repl
julia> fo = LibGit2.FetchOptions(
           proxy_opts = LibGit2.ProxyOptions(url = Cstring("https://my_proxy_url.com")))

julia> fetch(remote, "master", options=fo)
```
