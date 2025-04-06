```
DateTime(f::Function, y[, m, d, h, mi, s]; step=Day(1), limit=10000) -> DateTime
```

Bir `DateTime` oluşturun, ayarlayıcı API'si aracılığıyla. Başlangıç noktası, sağlanan `y, m, d...` argümanlarından oluşturulacak ve `f::Function` `true` döndürene kadar ayarlanacaktır. Ayarlamada adım boyutu, `step` anahtar kelimesi aracılığıyla manuel olarak sağlanabilir. `limit`, ayarlama API'sinin bir hata fırlatmadan önce takip edeceği maksimum iterasyon sayısına bir sınır sağlar (eğer `f::Function` asla tatmin edilmezse).

# Örnekler

```jldoctest
julia> DateTime(dt -> second(dt) == 40, 2010, 10, 20, 10; step = Second(1))
2010-10-20T10:00:40

julia> DateTime(dt -> hour(dt) == 20, 2010, 10, 20, 10; step = Hour(1), limit = 5)
HATA: ArgumentError: Ayarlama limiti aşıldı: 5 iterasyon
Stacktrace:
[...]
```
