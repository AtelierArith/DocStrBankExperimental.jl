```
LibGit2.git_url(; kwargs...) -> String
```

根据提供的 URL 组件创建一个字符串。当未提供 `scheme` 关键字时，生成的 URL 将使用替代的 [scp-like 语法](https://git-scm.com/docs/git-clone#_git_urls_a_id_urls_a)。

# 关键字

  * `scheme::AbstractString=""`: 用于标识所用协议的 URL 方案。对于 HTTP 使用 "http"，SSH 使用 "ssh" 等。当未提供 `scheme` 时，输出格式将为 "ssh"，但使用 scp-like 语法。
  * `username::AbstractString=""`: 如果提供，则在输出中使用的用户名。
  * `password::AbstractString=""`: 如果提供，则在输出中使用的密码。
  * `host::AbstractString=""`: 在输出中使用的主机名。必须指定主机名。
  * `port::Union{AbstractString,Integer}=""`: 如果提供，则在输出中使用的端口号。使用 scp-like 语法时无法指定。
  * `path::AbstractString=""`: 如果提供，则在输出中使用的路径。

!!! warning
    避免在 URL 中使用密码。与凭证对象不同，Julia 无法在使用后安全地清零或销毁敏感数据，密码可能会保留在内存中；可能会被未初始化的内存暴露。


# 示例

```jldoctest
julia> LibGit2.git_url(username="git", host="github.com", path="JuliaLang/julia.git")
"git@github.com:JuliaLang/julia.git"

julia> LibGit2.git_url(scheme="https", host="github.com", path="/JuliaLang/julia.git")
"https://github.com/JuliaLang/julia.git"

julia> LibGit2.git_url(scheme="ssh", username="git", host="github.com", port=2222, path="JuliaLang/julia.git")
"ssh://git@github.com:2222/JuliaLang/julia.git"
```
