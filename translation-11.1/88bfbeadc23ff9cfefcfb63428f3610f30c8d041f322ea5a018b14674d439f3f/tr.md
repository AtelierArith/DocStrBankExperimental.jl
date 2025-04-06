```
pointer(array [, index])
```

Bir dizinin veya stringin yerel adresini, isteğe bağlı olarak verilen `index` konumunda alır.

Bu fonksiyon "güvensizdir". Bu işaretçinin kullanılacağı süre boyunca `array` için bir Julia referansının var olduğundan emin olun. `array` argümanını belirli bir kod bloğu içinde çöp toplama işlemlerinden korumak için [`GC.@preserve`](@ref) makrosu kullanılmalıdır.

Genellikle [`Ref(array[, index])`](@ref Ref) çağrısı bu fonksiyondan daha tercih edilir çünkü geçerliliği garanti eder.
