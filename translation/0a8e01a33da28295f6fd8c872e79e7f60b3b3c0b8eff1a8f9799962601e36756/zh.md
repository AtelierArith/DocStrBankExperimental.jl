```
TCPSocket(; delay=true)
```

使用 libuv 打开一个 TCP 套接字。如果 `delay` 为真，libuv 会延迟创建套接字的文件描述符，直到第一次 [`bind`](@ref) 调用。`TCPSocket` 具有多个字段来表示套接字的状态以及其发送/接收缓冲区。
