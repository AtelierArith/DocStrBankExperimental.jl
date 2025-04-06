```
maxintfloat(T=Float64)
```

Verilen `T` kayan nokta türünde tam olarak temsil edilen en büyük ardışık tam sayı değerine sahip kayan nokta sayısıdır (varsayılan olarak `Float64`).

Yani, `maxintfloat`, `n+1`'in `T` türünde *tam olarak* temsil edilemediği en küçük pozitif tam sayı değerine sahip kayan nokta sayısı `n`'yi döndürür.

Bir `Integer` türü değeri gerektiğinde, `Integer(maxintfloat(T))` kullanın.
