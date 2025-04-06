```
open(filename::AbstractString, [mode::AbstractString]; lock = true) -> IOStream
```

Açık, beş boolean yerine bir dize tabanlı mod belirticisi kullanılan alternatif sözdizimi. `mode` değerleri, `fopen(3)` veya Perl `open`'den gelenlerle eşdeğerdir ve aşağıdaki boolean gruplarını ayarlamakla eşdeğerdir:

| Mod  | Açıklama                        | Anahtar Kelimeler              |
|:---- |:------------------------------- |:------------------------------ |
| `r`  | okuma                           | yok                            |
| `w`  | yazma, oluşturma, kesme         | `write = true`                 |
| `a`  | yazma, oluşturma, ekleme        | `append = true`                |
| `r+` | okuma, yazma                    | `read = true, write = true`    |
| `w+` | okuma, yazma, oluşturma, kesme  | `truncate = true, read = true` |
| `a+` | okuma, yazma, oluşturma, ekleme | `append = true, read = true`   |

`lock` anahtar kelime argümanı, işlemlerin güvenli çoklu iş parçacıklı erişim için kilitlenip kilitlenmeyeceğini kontrol eder.

# Örnekler

```jldoctest
julia> io = open("myfile.txt", "w");

julia> write(io, "Merhaba dünya!");

julia> close(io);

julia> io = open("myfile.txt", "r");

julia> read(io, String)
"Merhaba dünya!"

julia> write(io, "Bu dosya yalnızca okunabilir")
HATA: ArgumentError: yazma başarısız oldu, IOStream yazılabilir değil
[...]

julia> close(io)

julia> io = open("myfile.txt", "a");

julia> write(io, "Bu akış yalnızca okunabilir değil")
28

julia> close(io)

julia> rm("myfile.txt")
```

!!! uyumluluk "Julia 1.5"
    `lock` argümanı Julia 1.5 itibarıyla mevcuttur.

