```
cp(src::AbstractString, dst::AbstractString; force::Bool=false, follow_symlinks::Bool=false)
```

将文件、链接或目录从 `src` 复制到 `dst`。`force=true` 将首先删除现有的 `dst`。

如果 `follow_symlinks=false`，并且 `src` 是一个符号链接，则 `dst` 将作为符号链接创建。如果 `follow_symlinks=true` 并且 `src` 是一个符号链接，则 `dst` 将是 `src` 所指向的文件或目录的副本。返回 `dst`。

!!! note
    `cp` 函数与 `cp` 命令不同。`cp` 函数始终假设 `dst` 是一个文件，而命令则根据 `dst` 是目录还是文件执行不同的操作。当 `dst` 是一个目录时使用 `force=true` 将导致 `dst` 目录中所有内容的丢失，并且 `dst` 将变成一个包含 `src` 内容的文件。

