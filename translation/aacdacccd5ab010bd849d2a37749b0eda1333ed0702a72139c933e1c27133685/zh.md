```
LibGit2.RebaseOperation
```

描述在变基过程中要执行的单个指令/操作。与 [`git_rebase_operation`](https://libgit2.org/libgit2/#HEAD/type/git_rebase_operation_t) 结构匹配。

字段表示：

  * `optype`：当前正在执行的变基操作的类型。选项包括：

      * `REBASE_OPERATION_PICK`：挑选相关的提交。
      * `REBASE_OPERATION_REWORD`：挑选相关的提交，但使用提示重写其消息。
      * `REBASE_OPERATION_EDIT`：挑选相关的提交，但允许用户编辑提交的内容及其消息。
      * `REBASE_OPERATION_SQUASH`：将相关的提交压缩到前一个提交中。这两个提交的提交消息将被合并。
      * `REBASE_OPERATION_FIXUP`：将相关的提交压缩到前一个提交中。仅使用前一个提交的提交消息。
      * `REBASE_OPERATION_EXEC`：不挑选提交。运行一个命令，如果命令成功退出则继续。
  * `id`：在此变基步骤中正在处理的提交的 [`GitHash`](@ref)。
  * `exec`：如果使用 `REBASE_OPERATION_EXEC`，则在此步骤中要运行的命令（例如，在每个提交后运行测试套件）。
