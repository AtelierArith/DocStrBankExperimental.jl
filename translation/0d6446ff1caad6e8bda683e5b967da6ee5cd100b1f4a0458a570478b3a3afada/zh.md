```
getipaddr() -> IPAddr
```

获取本地机器的IP地址，优先选择IPv4而不是IPv6。如果没有可用的地址，则抛出异常。

```
getipaddr(addr_type::Type{T}) where T<:IPAddr -> T
```

获取本地机器的指定类型的IP地址。如果没有可用的指定类型的地址，则抛出异常。

此函数是对[`getipaddrs`](@ref)的向后兼容包装。新应用程序应使用[`getipaddrs`](@ref)代替。

# 示例

```julia-repl
julia> getipaddr()
ip"192.168.1.28"

julia> getipaddr(IPv6)
ip"fe80::9731:35af:e1c5:6e49"
```

另见[`getipaddrs`](@ref).
