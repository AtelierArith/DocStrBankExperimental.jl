```
cglobal((symbol, library) [, type=Cvoid])
```

C'den dışa aktarılan bir paylaşımlı kütüphanedeki bir global değişkenin işaretçisini elde edin, tam olarak [`ccall`](@ref) olarak belirtildiği gibi. Bir `Ptr{Type}` döner, eğer `Type` argümanı sağlanmazsa varsayılan olarak `Ptr{Cvoid}` kullanılır. Değerler [`unsafe_load`](@ref) veya [`unsafe_store!`](@ref) ile sırasıyla okunabilir veya yazılabilir.
