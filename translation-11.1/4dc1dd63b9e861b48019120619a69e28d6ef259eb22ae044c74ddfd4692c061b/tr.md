```
remotecall(f, id::Integer, args...; kwargs...) -> Future
```

Verilen argümanlar ile belirtilen süreçte bir `f` fonksiyonunu asenkron olarak çağırır. Bir [`Future`](@ref) döner. Varsa anahtar kelime argümanları `f`'ye iletilir.
