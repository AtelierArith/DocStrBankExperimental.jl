```
unsafe_wrap(Array, pointer::Ptr{T}, dims; own = false)
```

Bir Julia `Array` nesnesini `pointer` ile verilen adresteki verilere sarmalar, kopya oluşturmadan. Pointer eleman türü `T`, dizi eleman türünü belirler. `dims`, ya bir tam sayı (1d dizi için) ya da dizi boyutlarının bir demetidir. `own`, isteğe bağlı olarak, Julia'nın belleğin mülkiyetini alıp almayacağını belirtir; dizi artık referans edilmediğinde pointer üzerinde `free` çağrılır.

Bu işlev "güvensiz" olarak etiketlenmiştir çünkü `pointer`, istenen uzunluktaki verilere geçerli bir bellek adresi değilse çökmesine neden olur. [`unsafe_load`](@ref) ve [`unsafe_store!`](@ref) ile karşılaştırıldığında, programcı ayrıca altındaki verilere farklı eleman türlerine sahip iki dizi aracılığıyla erişilmediğinden emin olmaktan da sorumludur; bu, C'deki katı aliasing kuralına benzer.
