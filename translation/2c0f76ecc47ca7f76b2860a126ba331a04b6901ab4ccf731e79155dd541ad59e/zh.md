```
LibGit2.tag_create(repo::GitRepo, tag::AbstractString, commit; kwargs...)
```

在仓库 `repo` 中创建一个新的 git 标签 `tag`（例如 `"v0.5"`），位于提交 `commit` 处。

关键字参数包括：

  * `msg::AbstractString=""`：标签的消息。
  * `force::Bool=false`：如果为 `true`，将覆盖现有引用。
  * `sig::Signature=Signature(repo)`：标签创建者的签名。
