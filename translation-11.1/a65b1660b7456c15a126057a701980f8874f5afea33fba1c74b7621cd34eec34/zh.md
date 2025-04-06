```
getnameinfo(host::IPAddr) -> String
```

执行IP地址的反向查找，以使用操作系统的底层`getnameinfo`实现返回主机名和服务。

# 示例

```julia-repl
julia> getnameinfo(IPv4("8.8.8.8"))
"google-public-dns-a.google.com"
```
