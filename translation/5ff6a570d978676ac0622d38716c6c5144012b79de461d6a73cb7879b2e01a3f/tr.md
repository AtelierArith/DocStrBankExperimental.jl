```
RemoteChannel(pid::Integer=myid())
```

Bir `Channel{Any}(1)` referansı oluşturur, `pid` sürecinde. Varsayılan `pid`, mevcut süreçtir.

```
RemoteChannel(f::Function, pid::Integer=myid())
```

Belirli bir boyut ve türdeki uzak kanallara referanslar oluşturur. `f`, `pid` üzerinde çalıştırıldığında bir `AbstractChannel` uygulaması döndürmelidir.

Örneğin, `RemoteChannel(()->Channel{Int}(10), pid)`, `pid` üzerinde `Int` türünde ve boyutu 10 olan bir kanala referans döndürecektir.

Varsayılan `pid`, mevcut süreçtir.
