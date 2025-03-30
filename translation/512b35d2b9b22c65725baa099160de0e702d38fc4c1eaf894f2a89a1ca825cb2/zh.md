```
getaddrinfo(host::AbstractString, IPAddr) -> IPAddr
```

获取指定 `IPAddr` 类型的 `host` 的第一个 IP 地址。使用操作系统底层的 getaddrinfo 实现，可能会进行 DNS 查找。

# 示例

```julia-repl
julia> getaddrinfo("localhost", IPv6)
ip"::1"

julia> getaddrinfo("localhost", IPv4)
ip"127.0.0.1"
```
