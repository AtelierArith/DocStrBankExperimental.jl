```
setprecision([T=BigFloat,] precision::Int; base=2)
```

`T` aritmetiği için kullanılacak hassasiyeti (varsayılan olarak bit cinsinden) ayarlayın. `base` belirtilirse, o zaman hassasiyet, belirtilen `base`'de en az `precision` basamağı vermek için gereken minimum değerdir.

!!! uyarı     Bu fonksiyon thread-güvenli değildir. Tüm thread'lerde çalışan kodu etkileyecektir, ancak ayar ile birlikte hesaplamalarla eşzamanlı olarak çağrıldığında davranışı tanımsızdır.

!!! uyumluluk "Julia 1.8"
    `base` anahtar kelimesi en az Julia 1.8 gerektirir.

