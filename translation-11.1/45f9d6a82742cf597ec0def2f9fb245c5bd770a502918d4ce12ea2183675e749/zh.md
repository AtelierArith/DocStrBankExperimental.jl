```
push(rmt::GitRemote, refspecs; force::Bool=false, options::PushOptions=PushOptions())
```

推送到指定的 `rmt` 远程 git 仓库，使用 `refspecs` 来确定要推送到哪个远程分支。关键字参数包括：

  * `force`：如果为 `true`，将进行强制推送，忽略冲突。
  * `options`：确定推送的选项，例如使用哪些代理头。有关更多信息，请参见 [`PushOptions`](@ref)。

!!! note
    您可以通过两种其他方式添加有关推送 refspecs 的信息：通过在仓库的 `GitConfig` 中设置一个选项（以 `push.default` 作为键）或通过调用 [`add_push!`](@ref)。否则，您需要在调用 `push` 时明确指定推送 refspec，以使其生效，如下所示：`LibGit2.push(repo, refspecs=["refs/heads/master"])`。

