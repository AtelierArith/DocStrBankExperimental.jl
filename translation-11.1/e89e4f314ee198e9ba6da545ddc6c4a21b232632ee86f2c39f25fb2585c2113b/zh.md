```
listen([addr, ]port::Integer; backlog::Integer=BACKLOG_DEFAULT) -> TCPServer
```

在由 `addr` 指定的地址上监听端口。默认情况下，这仅在 `localhost` 上监听。要在所有接口上监听，请根据需要传递 `IPv4(0)` 或 `IPv6(0)`。`backlog` 决定在服务器开始拒绝连接之前可以有多少个待处理连接（尚未调用 [`accept`](@ref)）。`backlog` 的默认值为 511。
