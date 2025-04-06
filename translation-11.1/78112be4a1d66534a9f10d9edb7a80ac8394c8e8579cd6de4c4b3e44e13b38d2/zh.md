```
create(
    [ predicate, ] dir, [ tarball ];
    [ skeleton, ] [ portable = false ]
) -> tarball

    predicate :: String --> Bool
    dir       :: AbstractString
    tarball   :: Union{AbstractString, AbstractCmd, IO}
    skeleton  :: Union{AbstractString, AbstractCmd, IO}
    portable  :: Bool
```

创建目录 `dir` 的 tar 归档 ("tarball")。生成的归档写入路径 `tarball`，如果未指定路径，则创建一个临时路径并由函数调用返回。如果 `tarball` 是一个 IO 对象，则 tarball 内容将写入该句柄（句柄保持打开状态）。

如果传递了 `predicate` 函数，则在递归搜索 `dir` 时会对每个遇到的系统路径调用该函数，只有当 `predicate(path)` 为真时，`path` 才会包含在 tarball 中。如果 `predicate(path)` 对某个目录返回假，则该目录将被完全排除：该目录下的内容将不会包含在归档中。

如果传递了 `skeleton` 关键字，则给定的文件或 IO 句柄将用作生成 tarball 的 "骨架"。通过将 `skeleton` 关键字传递给 `extract` 命令来创建骨架文件。如果使用该骨架文件调用 `create`，并且提取的文件没有更改，则会重新创建一个相同的 tarball。`skeleton` 和 `predicate` 参数不能一起使用。

如果 `portable` 标志为真，则会检查路径名称在 Windows 上的有效性，以确保它们不包含非法字符或具有保留的名称。有关详细信息，请参见 https://stackoverflow.com/a/31976060/659248。
