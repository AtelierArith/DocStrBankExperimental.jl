```
fetch(rmt::GitRemote, refspecs; options::FetchOptions=FetchOptions(), msg="")
```

从指定的 `rmt` 远程 git 仓库中获取，使用 `refspecs` 来确定要获取的远程分支。关键字参数包括：

  * `options`: 确定获取的选项，例如是否在之后进行修剪。有关更多信息，请参见 [`FetchOptions`](@ref)。
  * `msg`: 插入到 reflogs 中的消息。
