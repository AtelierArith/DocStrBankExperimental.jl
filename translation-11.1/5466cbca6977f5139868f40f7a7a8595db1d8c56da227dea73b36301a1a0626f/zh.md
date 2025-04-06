```
merge!(repo::GitRepo, anns::Vector{GitAnnotated}, fastforward::Bool; kwargs...) -> Bool
```

将注释提交（作为 [`GitAnnotated`](@ref) 对象）`anns` 中的更改合并到仓库 `repo` 的 HEAD。如果 `fastforward` 为 `true`，则只允许快速合并。在这种情况下，如果发生冲突，合并将失败。否则，如果 `fastforward` 为 `false`，合并可能会产生一个冲突文件，用户需要解决该文件。

关键字参数包括：

  * `merge_opts::MergeOptions = MergeOptions()`: 执行合并的选项，包括是否允许快速合并。有关更多信息，请参见 [`MergeOptions`](@ref)。
  * `checkout_opts::CheckoutOptions = CheckoutOptions()`: 执行检出的选项。有关更多信息，请参见 [`CheckoutOptions`](@ref)。

`anns` 可以指远程或本地分支头。如果合并成功，则返回 `true`，否则返回 `false`（例如，如果由于分支没有共同祖先而无法合并）。

# 示例

```julia
upst_ann_1 = LibGit2.GitAnnotated(repo, "branch/a")

# 合并分支，快速合并
LibGit2.merge!(repo, [upst_ann_1], true)

# 合并冲突！
upst_ann_2 = LibGit2.GitAnnotated(repo, "branch/b")
# 合并分支，尝试快速合并
LibGit2.merge!(repo, [upst_ann_2], true) # 将返回 false
LibGit2.merge!(repo, [upst_ann_2], false) # 将返回 true
```
