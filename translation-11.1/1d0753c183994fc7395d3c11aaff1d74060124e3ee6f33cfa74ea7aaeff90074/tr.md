```
Date(f::Function, y[, m, d]; step=Day(1), limit=10000) -> Date
```

`Date`'i ayarlayıcı API'si aracılığıyla oluşturun. Başlangıç noktası, sağlanan `y, m, d` argümanlarından oluşturulacak ve `f::Function` doğru döndüğü sürece ayarlanacaktır. Ayarlamada adım boyutu, `step` anahtar kelimesi aracılığıyla manuel olarak sağlanabilir. `limit`, ayarlama API'sinin bir hata fırlatmadan önce takip edeceği maksimum yineleme sayısına bir sınır sağlar (verilen `f::Function` asla tatmin edilmezse).

# Örnekler

```jldoctest
julia> Date(date -> week(date) == 20, 2010, 01, 01)
2010-05-17

julia> Date(date -> year(date) == 2010, 2000, 01, 01)
2010-01-01

julia> Date(date -> month(date) == 10, 2000, 01, 01; limit = 5)
HATA: ArgumentError: Ayarlama limiti aşıldı: 5 yineleme
Stacktrace:
[...]
```
