```
hardlink(src::AbstractString, dst::AbstractString)
```

Mevcut bir kaynak dosyasına `src` adıyla `dst` adında bir sert bağlantı oluşturur. Hedef `dst` mevcut olmamalıdır.

Ayrıca bakınız: [`symlink`](@ref).

!!! uyumluluk "Julia 1.8"
    Bu yöntem Julia 1.8'de eklendi.

