```
Time(f::Function, h, mi=0; step::Period=Second(1), limit::Int=10000)
Time(f::Function, h, mi, s; step::Period=Millisecond(1), limit::Int=10000)
Time(f::Function, h, mi, s, ms; step::Period=Microsecond(1), limit::Int=10000)
Time(f::Function, h, mi, s, ms, us; step::Period=Nanosecond(1), limit::Int=10000)
```

`h, mi, s, ms, us` argümanlarından sağlanan başlangıç noktası ile `adjuster API` aracılığıyla bir `Time` oluşturun ve `f::Function` `true` döndürene kadar ayarlayın. Ayarlama için adım boyutu, `step` anahtar kelimesi aracılığıyla manuel olarak sağlanabilir. `limit`, ayarlama API'sinin bir hata fırlatmadan önce takip edeceği maksimum iterasyon sayısına bir sınır sağlar (eğer `f::Function` asla tatmin edilmezse). Verilen argümanlar için daha büyük hassasiyet sağlamak üzere varsayılan adımın ayarlanacağını unutmayın; yani, saat, dakika ve saniye argümanları sağlandığında, varsayılan adım `Second(1)` yerine `Millisecond(1)` olacaktır.

# Örnekler

```jldoctest
julia> Time(t -> minute(t) == 30, 20)
20:30:00

julia> Time(t -> minute(t) == 0, 20)
20:00:00

julia> Time(t -> hour(t) == 10, 3; limit = 5)
HATA: ArgumentError: Ayarlama limiti aşıldı: 5 iterasyon
Stacktrace:
[...]
```
