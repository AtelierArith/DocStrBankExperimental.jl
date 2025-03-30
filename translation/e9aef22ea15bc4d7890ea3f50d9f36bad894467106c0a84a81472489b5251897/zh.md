```
merge!(repo::GitRepo; kwargs...) -> Bool
```

对仓库 `repo` 执行 git 合并，将具有分歧历史的提交合并到当前分支。如果合并成功，则返回 `true`，否则返回 `false`。

关键字参数如下：

  * `committish::AbstractString=""`：合并 `committish` 中指定的提交。
  * `branch::AbstractString=""`：合并分支 `branch` 及其自与当前分支分歧以来的所有提交。
  * `fastforward::Bool=false`：如果 `fastforward` 为 `true`，则仅在合并为快进时才合并（当前分支头是要合并的提交的祖先），否则拒绝合并并返回 `false`。这相当于 git CLI 选项 `--ff-only`。
  * `merge_opts::MergeOptions=MergeOptions()`：`merge_opts` 指定合并的选项，例如在冲突情况下的合并策略。
  * `checkout_opts::CheckoutOptions=CheckoutOptions()`：`checkout_opts` 指定检出步骤的选项。

等同于 `git merge [--ff-only] [<committish> | <branch>]`。

!!! note
    如果您指定了 `branch`，则必须以引用格式进行，因为字符串将被转换为 `GitReference`。例如，如果您想合并分支 `branch_a`，您可以调用 `merge!(repo, branch="refs/heads/branch_a")`。

