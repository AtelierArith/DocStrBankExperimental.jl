```
watch_folder(path::AbstractString, timeout_s::Real=-1)
```

Bir dosya veya dizin `path`'te değişiklikleri izler ve bir değişiklik meydana gelene kadar veya `timeout_s` saniye geçene kadar devam eder. Bu fonksiyon dosya sistemini sorgulamaz ve bunun yerine işletim sisteminden (örneğin, Linux'ta inotify aracılığıyla) bildirim almak için platforma özgü işlevsellik kullanır. Ayrıntılar için aşağıda bağlantısı verilen NodeJS belgelerine bakın.

Bu, `unwatch_folder` aynı `path` üzerinde çağrılana kadar arka planda `path` için değişiklikleri izlemeye devam edecektir.

Dönen değer, ilk alanı değiştirilen dosyanın adı (varsa) ve ikinci alanı olayları belirten `renamed`, `changed` ve `timedout` boolean alanlarına sahip bir nesne olan bir çift olacaktır.

Bu fonksiyonun davranışı platformlar arasında biraz farklılık gösterir. Daha ayrıntılı bilgi için [https://nodejs.org/api/fs.html#fs_caveats](https://nodejs.org/api/fs.html#fs_caveats) adresine bakın.
