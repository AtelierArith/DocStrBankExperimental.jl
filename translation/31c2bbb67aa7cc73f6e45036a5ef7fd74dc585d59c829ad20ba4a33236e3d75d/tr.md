```
toprev(func::Function, dt::TimeType; step=Day(-1), limit=10000, same=false) -> TimeType
```

`dt`'yi, `func` `true` döndürene kadar en fazla `limit` iterasyon ile `step` artışları yaparak ayarlar. `func`, tek bir `TimeType` argümanı almalı ve bir [`Bool`](@ref) döndürmelidir. `same`, `dt`'nin `func`'u tatmin etmede dikkate alınmasına izin verir.
