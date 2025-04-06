```
watch_file(path::AbstractString, timeout_s::Real=-1)
```

`path` dosyasını veya dizinini değişiklikler için izleyin, bir değişiklik meydana gelene kadar veya `timeout_s` saniyesi dolana kadar. Bu fonksiyon dosya sistemini sorgulamaz ve bunun yerine işletim sisteminden (örneğin, Linux'ta inotify aracılığıyla) bildirim almak için platforma özgü işlevsellik kullanır. Aşağıda bağlantılı NodeJS belgelerine detaylar için bakın.

Dönen değer, dosyayı izleme sonucunu veren `renamed`, `changed` ve `timedout` boolean alanlarına sahip bir nesnedir.

Bu fonksiyonun davranışı platformlar arasında biraz farklılık gösterir. Daha ayrıntılı bilgi için [https://nodejs.org/api/fs.html#fs_caveats](https://nodejs.org/api/fs.html#fs_caveats) adresine bakın.
