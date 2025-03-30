```
push(repo::GitRepo; kwargs...)
```

将更新推送到 `repo` 的上游。

关键字参数包括：

  * `remote::AbstractString="origin"`：要推送到的上游远程的名称。
  * `remoteurl::AbstractString=""`：`remote` 的 URL。
  * `refspecs=AbstractString[]`：确定推送的属性。
  * `force::Bool=false`：确定推送是否为强制推送，覆盖远程分支。
  * `credentials=nothing`：在对私有 `remote` 进行身份验证时提供凭据和/或设置。
  * `callbacks=Callbacks()`：用户提供的回调和有效负载。

等同于 `git push [<remoteurl>|<repo>] [<refspecs>]`。
