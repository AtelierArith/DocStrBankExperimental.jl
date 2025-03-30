```
readavailable(stream)
```

Bir akıştan mevcut tamponlanmış verileri okuyun. Gerçek I/O, yalnızca daha önce tamponlanmış veri yoksa gerçekleştirilir. Sonuç bir `Vector{UInt8}`'dir.

!!! warning
    Dönen veri miktarı uygulama bağımlıdır; örneğin, dahili tampon boyutu seçimine bağlı olabilir. Genellikle [`read`](@ref) gibi diğer işlevler kullanılmalıdır.

