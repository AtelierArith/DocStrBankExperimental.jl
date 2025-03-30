```
islinklocaladdr(addr::IPAddr)
```

测试一个IP地址是否是链路本地地址。链路本地地址不保证在其网络段之外是唯一的，因此路由器不会转发它们。链路本地地址来自地址块 `169.254.0.0/16` 或 `fe80::/10`。

# 示例

```julia
filter(!islinklocaladdr, getipaddrs())
```
