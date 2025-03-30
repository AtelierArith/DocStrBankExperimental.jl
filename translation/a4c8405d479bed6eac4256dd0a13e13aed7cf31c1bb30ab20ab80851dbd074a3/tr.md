```
poll_fd(fd, timeout_s::Gerçek=-1; okunabilir=false, yazılabilir=false)
```

Bir dosya tanımlayıcısını `fd` okuma veya yazma uygunluğundaki değişiklikler için izleyin ve `timeout_s` saniye cinsinden verilen bir zaman aşımı ile.

Anahtar kelime argümanları, hangi okuma ve/veya yazma durumunun izleneceğini belirler; bunlardan en az biri `true` olarak ayarlanmalıdır.

Dönen değer, anketin sonucunu veren `okunabilir`, `yazılabilir` ve `zaman aşımına uğramış` boolean alanlarına sahip bir nesnedir.
