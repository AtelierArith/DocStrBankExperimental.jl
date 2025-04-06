```
getaddrinfo(host::AbstractString) -> IPAddr
```

获取 `host` 的第一个可用 IP 地址，该地址可以是 `IPv4` 或 `IPv6` 地址。使用操作系统底层的 getaddrinfo 实现，该实现可能会进行 DNS 查找。
