```
AsyncCondition()
```

Bir `AsyncCondition` oluşturun, bu, C'den `uv_async_send` çağrısıyla bildirim alındığında, onun üzerinde [`wait`](@ref) çağrısı yapan bekleyen görevleri uyandırır. Nesne kapatıldığında ([`close`](@ref) ile) bekleyen görevler bir hata ile uyandırılır. Hâlâ aktif olup olmadığını kontrol etmek için [`isopen`](@ref) kullanın.

Bu, gönderme ve bekleme iş parçaları arasında örtük bir edinme ve serbest bırakma bellek sıralaması sağlar.
