```
recvfrom(socket::UDPSocket) -> (host_port, data)
```

从指定的套接字读取一个 UDP 数据包，返回一个元组 `(host_port, data)`，其中 `host_port` 将是适当的 InetAddr{IPv4} 或 InetAddr{IPv6}。

!!! compat "Julia 1.3"
    在 Julia 1.3 版本之前，返回的第一个值是一个地址 (`IPAddr`)。在 1.3 版本中，它被更改为 `InetAddr`。

