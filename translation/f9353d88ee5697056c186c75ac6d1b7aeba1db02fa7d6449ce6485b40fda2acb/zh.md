```
rewrite(
    [ predicate, ] old_tarball, [ new_tarball ];
    [ portable = false, ]
) -> new_tarball

    predicate   :: Header --> Bool
    old_tarball :: Union{AbstractString, AbstractCmd, IO}
    new_tarball :: Union{AbstractString, AbstractCmd, IO}
    portable    :: Bool
```

将 `old_tarball` 重写为 `create` 生成的标准格式，同时检查它是否包含任何会导致 `extract` 引发错误的内容。这在功能上等同于执行

```
Tar.create(Tar.extract(predicate, old_tarball), new_tarball)
```

然而，它从不将任何内容提取到磁盘，而是使用 `seek` 函数来导航旧 tarball 的数据。如果没有传递 `new_tarball` 参数，则新 tarball 将写入一个临时文件，并返回其路径。

如果传递了 `predicate` 函数，则在提取 `old_tarball` 时会对每个遇到的 `Header` 对象调用该函数，除非 `predicate(hdr)` 为真，否则该条目将被跳过。这可以用于选择性地重写存档的某些部分，跳过会导致 `extract` 抛出错误的条目，或记录在重写过程中遇到的内容。

在传递给谓词函数之前，`Header` 对象会从 tarball 的原始头部进行一些修改：`path` 字段被规范化以删除 `.` 条目，并将多个连续的斜杠替换为一个斜杠。如果条目的类型为 `:hardlink`，则链接目标路径也以相同方式规范化，以便与目标条目的路径匹配；大小字段设置为目标路径的大小（该路径必须是已见过的文件）。

如果 `portable` 标志为真，则会检查路径名称在 Windows 上的有效性，以确保它们不包含非法字符或具有保留的名称。有关详细信息，请参见 https://stackoverflow.com/a/31976060/659248。
