```
LibGit2.CloneOptions
```

匹配 [`git_clone_options`](https://libgit2.org/libgit2/#HEAD/type/git_clone_options) 结构体。

字段表示：

  * `version`：正在使用的结构体版本，以防将来更改。目前始终为 `1`。
  * `checkout_opts`：作为克隆的一部分执行远程检出的选项。
  * `fetch_opts`：作为克隆的一部分执行远程预检索的选项。
  * `bare`：如果为 `0`，则克隆完整的远程仓库。如果非零，则执行裸克隆，其中在仓库中没有源文件的本地副本，且 [`gitdir`](@ref) 和 [`workdir`](@ref) 是相同的。
  * `localclone`：标志是否克隆本地对象数据库或进行检索。默认情况下让 git 决定。它不会为本地克隆使用 git 感知的传输，但会为以 `file://` 开头的 URL 使用。
  * `checkout_branch`：要检出的分支名称。如果为空字符串，则将检出远程的默认分支。
  * `repository_cb`：一个可选的回调，用于创建克隆所做的新仓库。
  * `repository_cb_payload`：仓库回调的有效负载。
  * `remote_cb`：一个可选的回调，用于在从中进行克隆之前创建 [`GitRemote`](@ref)。
  * `remote_cb_payload`：远程回调的有效负载。
