```
pointer_from_objref(x)
```

Bir Julia nesnesinin bellek adresini `Ptr` olarak alır. Elde edilen `Ptr` nesneyi çöp toplama işlemlerinden korumaz, bu nedenle `Ptr`'nin kullanılacağı süre boyunca nesnenin referansının devam etmesini sağlamalısınız.

Bu fonksiyon, kararlı bellek adreslerine sahip olmadıkları için değiştirilemez nesneler üzerinde çağrılmamalıdır.

Ayrıca bkz. [`unsafe_pointer_to_objref`](@ref).
