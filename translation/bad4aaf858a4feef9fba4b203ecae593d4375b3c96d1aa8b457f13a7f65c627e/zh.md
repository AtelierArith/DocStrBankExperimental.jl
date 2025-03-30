```
extract(
    [ predicate, ] tarball, [ dir ];
    [ skeleton = <none>, ]
    [ copy_symlinks = <auto>, ]
    [ set_permissions = true, ]
) -> dir

    predicate       :: Header --> Bool
    tarball         :: Union{AbstractString, AbstractCmd, IO}
    dir             :: AbstractString
    skeleton        :: Union{AbstractString, AbstractCmd, IO}
    copy_symlinks   :: Bool
    set_permissions :: Bool
```

将位于路径 `tarball` 的 tar 归档（“tarball”）提取到目录 `dir` 中。如果 `tarball` 是一个 IO 对象而不是路径，则归档内容将从该 IO 流中读取。归档被提取到 `dir`，该目录必须是一个已存在的空目录或一个可以创建为新目录的不存在路径。如果未指定 `dir`，则归档将提取到一个临时目录中，该目录由 `extract` 返回。

如果传递了 `predicate` 函数，则在提取 `tarball` 时遇到的每个 `Header` 对象上调用该函数，只有当 `predicate(hdr)` 为真时，条目才会被提取。这可以用于选择性地提取归档的某些部分，跳过导致 `extract` 抛出错误的条目，或记录在提取过程中提取的内容。

在传递给谓词函数之前，`Header` 对象会从 tarball 的原始头部进行一些修改：`path` 字段被规范化以删除 `.` 条目，并将多个连续的斜杠替换为一个斜杠。如果条目的类型为 `:hardlink`，则链接目标路径以相同方式规范化，以便与目标条目的路径匹配；大小字段设置为目标路径的大小（该路径必须是已见过的文件）。

如果传递了 `skeleton` 关键字，则提取的 tarball 的“骨架”将写入给定的文件或 IO 句柄。此骨架文件可用于通过将 `skeleton` 关键字传递给 `create` 函数来重建一个相同的 tarball。`skeleton` 和 `predicate` 参数不能一起使用。

如果 `copy_symlinks` 为 `true`，则不会将符号链接提取为符号链接，而是将其提取为它们链接到的内容的副本（如果它们在 tarball 内部并且可以这样做）。非内部符号链接，例如指向 `/etc/passwd` 的链接将不会被复制。以任何方式循环的符号链接也将不会被复制，而是会被跳过。默认情况下，`extract` 将检测是否可以在 `dir` 中创建符号链接，并在无法创建时自动复制符号链接。

如果 `set_permissions` 为 `false`，则不对提取的文件设置任何权限。
