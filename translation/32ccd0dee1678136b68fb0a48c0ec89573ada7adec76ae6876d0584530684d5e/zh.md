```
tree_hash([ predicate, ] tarball;
          [ algorithm = "git-sha1", ]
          [ skip_empty = false ]) -> hash::String

    predicate  :: Header --> Bool
    tarball    :: Union{AbstractString, AbstractCmd, IO}
    algorithm  :: AbstractString
    skip_empty :: Bool
```

计算 tarball 中包含的文件树的树哈希值。默认情况下，这使用 git 的树哈希算法和 SHA1 安全哈希函数（如当前版本的 git）。这意味着对于任何 git 可以表示的 tarball 的文件树——即仅包含文件、符号链接和非空目录的 tarball——此函数计算的哈希值将与 git 为该文件树计算的哈希值相同。请注意，tarball 可以表示包含空目录的文件树，而 git 无法存储这些空目录，此函数可以为这些空目录生成哈希，默认情况下（请参见 `skip_empty` 下面如何更改此行为）与省略这些空目录的 tarball 的哈希不同。简而言之，哈希函数在 git 可以表示的所有树上与 git 一致，但以一致的方式扩展了可哈希树的域到 git 无法表示的其他树。

如果传递了 `predicate` 函数，则在处理 `tarball` 时会对每个遇到的 `Header` 对象调用该函数，只有当 `predicate(hdr)` 为真时，条目才会被哈希。这可以用于选择性地仅哈希归档的某些部分，跳过导致 `extract` 抛出错误的条目，或记录在哈希过程中提取的内容。

在传递给谓词函数之前，`Header` 对象会从 tarball 的原始头部进行一些修改：`path` 字段被规范化以删除 `.` 条目，并将多个连续的斜杠替换为一个斜杠。如果条目的类型为 `:hardlink`，则链接目标路径以相同方式规范化，以便与目标条目的路径匹配；大小字段设置为目标路径的大小（该路径必须是已见过的文件）。

当前支持的 `algorithm` 值为 `git-sha1`（默认）和 `git-sha256`，后者使用与 `git-sha1` 相同的基本算法，但将 SHA1 哈希函数替换为 SHA2-256，这是 git 将在未来过渡使用的哈希函数（由于对 SHA1 的已知攻击）。未来可能会添加对其他文件树哈希算法的支持。

`skip_empty` 选项控制是否将递归不包含文件或符号链接的 tarball 中的目录包含在哈希中或忽略。一般来说，如果您正在哈希 tarball 或文件树的内容，您关心的是所有目录，而不仅仅是非空目录，因此将这些目录包含在计算的哈希中是默认行为。那么，为什么这个函数甚至提供跳过空目录的选项呢？因为 git 拒绝存储空目录，如果您尝试将它们添加到仓库中，它将忽略它们。因此，如果您通过将文件添加到 git 仓库来计算参考树哈希，然后请求 git 获取树哈希，您获得的哈希值将与 `skip_empty=true` 的 `tree_hash` 计算的哈希值匹配。换句话说，此选项允许 `tree_hash` 模拟 git 如何哈希包含空目录的树。然而，如果您正在哈希可能包含空目录的树（即不来自 git 仓库），建议您使用不忽略空目录的工具（例如此工具）进行哈希。
