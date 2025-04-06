```
isdone(itr, [state]) -> Union{Bool, Missing}
```

Bu fonksiyon, yineleyici tamamlanması için hızlı bir yol ipucu sağlar. Bu, kullanıcıya sunulmayacaksa elemanların tüketilmesini önlemek isteyen durumlu yineleyiciler için yararlıdır (örneğin, `isempty` veya `zip` içinde tamamlanma kontrolü yaparken).

Bu özelliği kullanmak isteyen durumlu yineleyiciler, yineleyicinin tamamlanıp tamamlanmadığına bağlı olarak doğru/yanlış döndüren bir `isdone` yöntemi tanımlamalıdır. Durumsuz yineleyicilerin bu fonksiyonu uygulaması gerekmez.

Sonuç `missing` ise, çağıranlar kesin bir cevap elde etmek için `iterate(x, state) === nothing` hesaplamaya devam edebilir.

Ayrıca bkz. [`iterate`](@ref), [`isempty`](@ref)
