```
connect(path::AbstractString) -> PipeEndpoint
```

连接到 `path` 处的命名管道 / UNIX 域套接字。

!!! note
    在 Unix 上，路径长度限制在 92 到 108 字节之间（参见 `man unix`）。

