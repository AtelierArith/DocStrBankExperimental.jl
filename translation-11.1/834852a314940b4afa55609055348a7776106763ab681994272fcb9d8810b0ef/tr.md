```
bind(socket::Union{TCPServer, UDPSocket, TCPSocket}, host::IPAddr, port::Integer; ipv6only=false, reuseaddr=false, kws...)
```

`socket`'ı verilen `host:port`'a bağlayın. `0.0.0.0`'ın tüm cihazlarda dinleyeceğini unutmayın.

  * `ipv6only` parametresi çift yığın modunu devre dışı bırakır. Eğer `ipv6only=true` ise, yalnızca bir IPv6 yığını oluşturulur.
  * Eğer `reuseaddr=true` ise, birden fazla iş parçacığı veya işlem aynı adrese hata vermeden bağlanabilir, ancak yalnızca en son bağlanan trafik alacaktır.
