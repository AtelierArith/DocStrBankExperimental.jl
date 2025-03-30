```
recvfrom(socket::UDPSocket) -> (host_port, data)
```

Belirtilen soketten bir UDP paketi okuyun ve `(host_port, data)` şeklinde bir demet döndürün; burada `host_port`, uygun olduğunda bir InetAddr{IPv4} veya InetAddr{IPv6} olacaktır.

!!! compat "Julia 1.3"
    Julia sürüm 1.3'ten önce, döndürülen ilk değer bir adresdi (`IPAddr`). Sürüm 1.3'te `InetAddr` olarak değiştirildi.

