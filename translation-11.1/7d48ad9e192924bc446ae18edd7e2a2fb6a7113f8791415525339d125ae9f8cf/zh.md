```
getipaddrs(addr_type::Type{T}=IPAddr; loopback::Bool=false) where T<:IPAddr -> Vector{T}
```

获取本地机器的 IP 地址。

将可选的 `addr_type` 参数设置为 `IPv4` 或 `IPv6` 会导致仅返回该类型的地址。

`loopback` 关键字参数决定是否包含回环地址（例如 `ip"127.0.0.1"`，`ip"::1"`）。

!!! compat "Julia 1.2"
    此函数自 Julia 1.2 起可用。


# 示例

```julia-repl
julia> getipaddrs()
5-element Array{IPAddr,1}:
 ip"198.51.100.17"
 ip"203.0.113.2"
 ip"2001:db8:8:4:445e:5fff:fe5d:5500"
 ip"2001:db8:8:4:c164:402e:7e3c:3668"
 ip"fe80::445e:5fff:fe5d:5500"

julia> getipaddrs(IPv6)
3-element Array{IPv6,1}:
 ip"2001:db8:8:4:445e:5fff:fe5d:5500"
 ip"2001:db8:8:4:c164:402e:7e3c:3668"
 ip"fe80::445e:5fff:fe5d:5500"
```

另见 [`islinklocaladdr`](@ref).
