```
realpath(path::AbstractString) -> String
```

通过展开符号链接并删除“.”和“..”条目来规范化路径。在不区分大小写且保留大小写的文件系统（通常是 Mac 和 Windows）上，将返回路径的存储大小写。

（如果 `path` 在文件系统中不存在，此函数会抛出异常。）
