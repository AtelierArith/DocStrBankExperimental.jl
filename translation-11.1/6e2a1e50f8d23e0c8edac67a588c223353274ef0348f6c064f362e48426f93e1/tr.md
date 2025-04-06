```
Base.checked_abs(x)
```

`abs(x)` değerini hesaplar, uygun yerlerde taşma hatalarını kontrol eder. Örneğin, standart iki'nin tamamlayanı işaretli tam sayılar (örneğin `Int`), `abs(typemin(Int))` değerini temsil edemez, bu da bir taşmaya yol açar.

Taşma koruması, algılanabilir bir performans cezası getirebilir.
