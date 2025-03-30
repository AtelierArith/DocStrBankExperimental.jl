```
dt::Date + t::Time -> DateTime
```

Bir `Date` ile bir `Time`'ın toplanması bir `DateTime` üretir. `Time`'ın saat, dakika, saniye ve milisaniye kısımları, yeni `DateTime`'ı oluşturmak için `Date`'in yıl, ay ve günü ile birlikte kullanılır. `Time` türündeki sıfırdan farklı mikro saniyeler veya nano saniyeler bir `InexactError` hatasının fırlatılmasına neden olacaktır.
