```
mkfifo(path::AbstractString, [mode::Integer]) -> path
```

在 `path` 处创建一个 FIFO 特殊文件（命名管道）。成功时返回 `path` 原样。

`mkfifo` 仅在 Unix 平台上受支持。

!!! compat "Julia 1.11"
    `mkfifo` 至少需要 Julia 1.11。

