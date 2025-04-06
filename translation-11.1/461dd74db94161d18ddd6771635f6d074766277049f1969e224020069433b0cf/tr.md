```
setrounding(T, mode)
```

`T` türündeki kayan nokta sayısının yuvarlama modunu ayarlar ve temel aritmetik fonksiyonların ([`+`](@ref), [`-`](@ref), [`*`](@ref), [`/`](@ref) ve [`sqrt`](@ref)) ve tür dönüşümünün yuvarlamasını kontrol eder. Varsayılan [`RoundNearest`](@ref) dışındaki yuvarlama modları kullanıldığında diğer sayısal fonksiyonlar yanlış veya geçersiz değerler verebilir.

Bu durumun şu anda yalnızca `T == BigFloat` için desteklendiğini unutmayın.

!!! warning
    Bu fonksiyon thread güvenli değildir. Tüm thread'lerde çalışan kodu etkileyecektir, ancak ayar ile birlikte hesaplamalarla eşzamanlı olarak çağrıldığında davranışı tanımsızdır.

