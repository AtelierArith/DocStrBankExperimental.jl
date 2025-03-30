```
listen([addr, ]port::Integer; backlog::Integer=BACKLOG_DEFAULT) -> TCPServer
```

Belirtilen `addr` adresinde portta dinleyin. Varsayılan olarak bu yalnızca `localhost` üzerinde dinler. Tüm arayüzlerde dinlemek için uygun şekilde `IPv4(0)` veya `IPv6(0)` geçirin. `backlog`, sunucunun reddetmeye başlamadan önce bekleyen (henüz [`accept`](@ref) çağrılmamış) kaç bağlantının olabileceğini belirler. `backlog`'un varsayılan değeri 511'dir.
