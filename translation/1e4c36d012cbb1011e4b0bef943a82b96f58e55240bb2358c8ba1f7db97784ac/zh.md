```
relpath(path::AbstractString, startpath::AbstractString = ".") -> String
```

返回相对于当前目录或可选起始目录的 `path` 的相对文件路径。这是一个路径计算：不访问文件系统以确认 `path` 或 `startpath` 的存在或性质。

在 Windows 上，路径的每个部分都应用大小写敏感性，除了驱动器字母。如果 `path` 和 `startpath` 指向不同的驱动器，则返回 `path` 的绝对路径。
