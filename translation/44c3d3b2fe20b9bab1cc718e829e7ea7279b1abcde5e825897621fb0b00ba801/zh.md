```
nagle(socket::Union{TCPServer, TCPSocket}, enable::Bool)
```

纳格尔算法将多个小的 TCP 数据包批量处理成更大的数据包。这可以提高吞吐量，但会恶化延迟。纳格尔算法默认启用。此函数设置给定 TCP 服务器或套接字上是否启用纳格尔算法。相反的选项在其他语言中称为 `TCP_NODELAY`。

!!! compat "Julia 1.3"
    此函数需要 Julia 1.3 或更高版本。

