```
connect(manager::ClusterManager, pid::Int, config::WorkerConfig) -> (instrm::IO, outstrm::IO)
```

Özel taşımalar kullanan küme yöneticileri tarafından uygulanmıştır. `config` tarafından belirtilen `pid` kimliğine sahip işçiye mantıksal bir bağlantı kurmalıdır ve bir çift `IO` nesnesi döndürmelidir. `pid`'den mevcut işleme gelen mesajlar `instrm` üzerinden okunacakken, `pid`'ye gönderilecek mesajlar `outstrm`'ye yazılacaktır. Özel taşımacılık uygulaması, mesajların tamamen ve sıralı bir şekilde teslim edilmesini ve alınmasını sağlamalıdır. `connect(manager::ClusterManager.....)` işçiler arasında TCP/IP soket bağlantıları kurar.
