```
listen(path::AbstractString) -> PipeServer
```

创建并监听一个命名管道 / UNIX 域套接字。

!!! note
    在 Unix 上，路径长度限制在 92 到 108 字节之间（参见 `man unix`）。

