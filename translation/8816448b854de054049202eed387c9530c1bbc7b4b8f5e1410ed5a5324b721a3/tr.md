```
randjump(r::MersenneTwister, steps::Integer) -> MersenneTwister
```

Başlatılmış bir `MersenneTwister` nesnesi oluşturur; bu nesnenin durumu, `r`'den `steps` adım ileriye taşınır (sayılar üretilmeden). Her bir adım, iki `Float64` sayısının üretilmesine karşılık gelir. Farklı `steps` değerleri için, dahili olarak büyük bir polinom üretilmesi gerekir. `steps=big(10)^20` için bir tanesi zaten önceden hesaplanmıştır.
