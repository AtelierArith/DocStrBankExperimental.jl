```
LibGit2.FetchHead
```

包含有关获取期间 HEAD 的信息，包括从中获取的分支的名称和 URL、HEAD 的 oid，以及获取的 HEAD 是否已在本地合并。

字段表示：

  * `name`: 获取头在本地引用数据库中的名称，例如 `"refs/heads/master"`。
  * `url`: 获取头的 URL。
  * `oid`: 获取头尖端的 [`GitHash`](@ref)。
  * `ismerge`: 布尔标志，指示远程的更改是否已合并到本地副本中。如果为 `true`，则本地副本与远程获取头是最新的。
