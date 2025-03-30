```
open(filename::AbstractString; lock = true, keywords...) -> IOStream
```

Beş boolean anahtar argümanla belirtilen bir modda bir dosya açın:

| Anahtar    | Açıklama              | Varsayılan                            |
|:---------- |:--------------------- |:------------------------------------- |
| `read`     | okuma için aç         | `!write`                              |
| `write`    | yazma için aç         | `truncate \| append`                  |
| `create`   | yoksa oluştur         | `!read & write \| truncate \| append` |
| `truncate` | sıfır boyutuna kısalt | `!read & write`                       |
| `append`   | sona git              | `false`                               |

Anahtar kelimeler geçilmediğinde varsayılan olarak dosyalar yalnızca okuma için açılır. Açılan dosyaya erişim için bir akış döner.

`lock` anahtar argümanı, işlemlerin güvenli çoklu iş parçacıklı erişim için kilitlenip kilitlenmeyeceğini kontrol eder.

!!! compat "Julia 1.5"
    `lock` argümanı Julia 1.5 itibarıyla mevcuttur.

