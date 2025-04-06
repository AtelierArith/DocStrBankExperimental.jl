```
merge!(repo::GitRepo, anns::Vector{GitAnnotated}; kwargs...) -> Bool
```

将注释提交（作为 [`GitAnnotated`](@ref) 对象捕获）的更改 `anns` 合并到仓库 `repo` 的 HEAD。关键字参数包括：

  * `merge_opts::MergeOptions = MergeOptions()`: 执行合并的选项，包括是否允许快速前进。有关更多信息，请参见 [`MergeOptions`](@ref)。
  * `checkout_opts::CheckoutOptions = CheckoutOptions()`: 执行检出操作的选项。有关更多信息，请参见 [`CheckoutOptions`](@ref)。

`anns` 可以指远程或本地分支头。如果合并成功，则返回 `true`，否则返回 `false`（例如，如果由于分支没有共同祖先而无法合并）。

# 示例

```julia
upst_ann = LibGit2.GitAnnotated(repo, "branch/a")

# 合并该分支
LibGit2.merge!(repo, [upst_ann])
```
