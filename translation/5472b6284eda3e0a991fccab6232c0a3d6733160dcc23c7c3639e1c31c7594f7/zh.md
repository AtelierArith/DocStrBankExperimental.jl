```
process_messages(r_stream::IO, w_stream::IO, incoming::Bool=true)
```

由集群管理器使用自定义传输调用。当自定义传输实现接收到来自远程工作者的第一条消息时，应调用此函数。自定义传输必须管理与远程工作者的逻辑连接，并提供两个 `IO` 对象，一个用于传入消息，另一个用于发往远程工作者的消息。如果 `incoming` 为 `true`，则表示远程对等方发起了连接。无论哪一方发起连接，都将发送集群 cookie 及其 Julia 版本号以执行身份验证握手。

另见 [`cluster_cookie`](@ref).
