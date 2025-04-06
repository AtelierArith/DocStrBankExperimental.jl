```
methodswith(typ[, modül veya fonksiyon]; üsttipler::Bool=false])
```

`typ` türünde bir argüman ile yöntemlerin bir dizisini döndürür.

İsteğe bağlı ikinci argüman, aramayı belirli bir modül veya fonksiyonla sınırlamak için kullanılır (varsayılan, tüm üst düzey modüllerdir).

`üsttipler` anahtar kelimesi `true` ise, `Any` türü hariç, `typ` türünün bir üst türüne sahip argümanları da döndürür.

Ayrıca bkz: [`methods`](@ref).
