```
LibGit2.RebaseOptions
```

匹配 `git_rebase_options` 结构体。

字段表示：

  * `version`：正在使用的结构体版本，以防将来更改。目前始终为 `1`。
  * `quiet`：通知其他 git 客户端在进行 rebase 时应“安静”地完成 rebase。用于互操作性。默认值为 `1`。
  * `inmemory`：开始一个内存中的 rebase。处理 rebase 的调用者可以逐步进行并提交任何更改，但不能回退 HEAD 或更新仓库。[`workdir`](@ref) 将不会被修改。仅在 libgit2 版本大于或等于 0.24.0 时存在。
  * `rewrite_notes_ref`：用于在 rebase 完成时重写提交注释的注释引用名称。
  * `merge_opts`：控制在每个 rebase 步骤中如何合并树的合并选项。仅在 libgit2 版本大于或等于 0.24.0 时存在。
  * `checkout_opts`：在初始化 rebase、逐步进行和中止时写入文件的检出选项。有关更多信息，请参见 [`CheckoutOptions`](@ref)。
