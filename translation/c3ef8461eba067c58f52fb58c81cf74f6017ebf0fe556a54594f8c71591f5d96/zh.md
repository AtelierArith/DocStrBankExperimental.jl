```
fetch(repo::GitRepo; kwargs...)
```

从仓库 `repo` 的上游获取更新。

关键字参数包括：

  * `remote::AbstractString="origin"`：要从中获取的 `repo` 的远程名称。如果为空，将使用 URL 构造一个匿名远程。
  * `remoteurl::AbstractString=""`：`remote` 的 URL。如果未指定，将根据给定的 `remote` 名称进行假设。
  * `refspecs=AbstractString[]`：确定获取的属性。
  * `credentials=nothing`：在对私有 `remote` 进行身份验证时提供凭据和/或设置。
  * `callbacks=Callbacks()`：用户提供的回调和有效负载。

等同于 `git fetch [<remoteurl>|<repo>] [<refspecs>]`。
