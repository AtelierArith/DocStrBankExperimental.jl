```
getalladdrinfo(host::AbstractString) -> Vector{IPAddr}
```

获取 `host` 的所有 IP 地址。使用操作系统底层的 `getaddrinfo` 实现，这可能会进行 DNS 查找。

# 示例

```julia-repl
julia> getalladdrinfo("google.com")
2-element Array{IPAddr,1}:
 ip"172.217.6.174"
 ip"2607:f8b0:4000:804::200e"
```
