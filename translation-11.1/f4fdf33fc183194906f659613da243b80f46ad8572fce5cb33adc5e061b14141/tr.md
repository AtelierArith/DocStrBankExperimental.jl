```
setopt(sock::UDPSocket; multicast_loop=nothing, multicast_ttl=nothing, enable_broadcast=nothing, ttl=nothing)
```

UDP soket seçeneklerini ayarlayın.

  * `multicast_loop`: çoklu yayım paketleri için geri döngü (varsayılan: `true`).
  * `multicast_ttl`: çoklu yayım paketleri için TTL (varsayılan: `nothing`).
  * `enable_broadcast`: soket yayın mesajları için kullanılacaksa `true` olarak ayarlanmalıdır, aksi takdirde UDP sistemi bir erişim hatası döndürecektir (varsayılan: `false`).
  * `ttl`: soket üzerinden gönderilen paketlerin yaşam süresi (varsayılan: `nothing`).
