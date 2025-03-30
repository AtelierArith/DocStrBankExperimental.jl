```
bind(socket::Union{TCPServer, UDPSocket, TCPSocket}, host::IPAddr, port::Integer; ipv6only=false, reuseaddr=false, kws...)
```

将 `socket` 绑定到给定的 `host:port`。请注意，`0.0.0.0` 将在所有设备上监听。

  * `ipv6only` 参数禁用双栈模式。如果 `ipv6only=true`，则只会创建一个 IPv6 栈。
  * 如果 `reuseaddr=true`，多个线程或进程可以在不出错的情况下绑定到同一地址，只要它们都设置 `reuseaddr=true`，但只有最后一个绑定的将接收任何流量。
