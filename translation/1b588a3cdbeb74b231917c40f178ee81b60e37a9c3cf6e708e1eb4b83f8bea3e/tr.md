```
Fonksiyon
```

Tüm fonksiyonların soyut türü.

# Örnekler

```jldoctest
julia> isa(+, Function)
true

julia> typeof(sin)
typeof(sin) (sin fonksiyonunun tekil türü, Function alt türü)

julia> ans <: Function
true
```
