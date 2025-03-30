```
setopt(sock::UDPSocket; multicast_loop=nothing, multicast_ttl=nothing, enable_broadcast=nothing, ttl=nothing)
```

设置 UDP 套接字选项。

  * `multicast_loop`: 多播数据包的回环（默认值：`true`）。
  * `multicast_ttl`: 多播数据包的 TTL（默认值：`nothing`）。
  * `enable_broadcast`: 如果套接字将用于广播消息，则必须将标志设置为 `true`，否则 UDP 系统将返回访问错误（默认值：`false`）。
  * `ttl`: 通过套接字发送的数据包的生存时间（默认值：`nothing`）。
