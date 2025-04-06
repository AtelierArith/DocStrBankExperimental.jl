```
precision(num::AbstractFloat; base::Integer=2)
precision(T::Type; base::Integer=2)
```

Bir kayan nokta sayısının hassasiyetini, anlamlı basamaklardaki etkili bit sayısı olarak tanımlar veya bir kayan nokta türü `T` için hassasiyeti döner (eğer `T`, [`BigFloat`](@ref) gibi değişken hassasiyetli bir türse, mevcut varsayılanı).

Eğer `base` belirtilmişse, o zaman o tabandaki maksimum karşılık gelen anlamlı basamak sayısını döner.

!!! uyumluluk "Julia 1.8"
    `base` anahtar kelimesi en az Julia 1.8 gerektirir.

