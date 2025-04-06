```
listenany([host::IPAddr,] port_hint; backlog::Integer=BACKLOG_DEFAULT) -> (UInt16, TCPServer)
```

Herhangi bir portta bir `TCPServer` oluşturun, ipucu başlangıç noktası olarak kullanılır. Sunucunun oluşturulduğu gerçek port ve sunucunun kendisi bir demet olarak döndürülür. backlog argümanı, sockfd için bekleyen bağlantıların kuyruğunun büyüyebileceği maksimum uzunluğu tanımlar.
