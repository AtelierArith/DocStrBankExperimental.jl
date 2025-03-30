```
mktempdir(f::Function, parent=tempdir(); prefix="jl_")
```

Fonksiyonu `f`'yi [`mktempdir(parent; prefix)`](@ref) sonucuna uygular ve tamamlandığında geçici dizini ve tüm içeriğini kaldırır.

Ayrıca bakınız: [`mktemp`](@ref), [`mkdir`](@ref).

!!! uyumluluk "Julia 1.2"
    `prefix` anahtar argümanı Julia 1.2'de eklendi.

