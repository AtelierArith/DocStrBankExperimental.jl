```
LibGit2.SignatureStruct
```

一个操作签名（例如，提交者、标签者等）。与 [`git_signature`](https://libgit2.org/libgit2/#HEAD/type/git_signature) 结构匹配。

字段表示：

  * `name`: 提交者或提交的作者的全名。
  * `email`: 可以联系到提交者/作者的电子邮件。
  * `when`: 一个 [`TimeStruct`](@ref)，指示提交何时被创作/提交到仓库。
