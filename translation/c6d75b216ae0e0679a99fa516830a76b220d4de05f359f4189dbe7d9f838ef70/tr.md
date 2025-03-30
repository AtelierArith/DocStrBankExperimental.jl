```
Base.checked_neg(x)
```

`-x` hesaplar, uygun yerlerde taşma hatalarını kontrol eder. Örneğin, standart iki'nin tamamlayanı işaretli tam sayılar (örneğin `Int`) `-typemin(Int)` değerini temsil edemez, bu da bir taşmaya yol açar.

Taşma koruması, algılanabilir bir performans cezası getirebilir.
