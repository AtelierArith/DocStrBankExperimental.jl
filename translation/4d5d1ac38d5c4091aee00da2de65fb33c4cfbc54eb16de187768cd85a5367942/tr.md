```
>(x, y)
```

Büyüktür karşılaştırma operatörü. `y < x` ifadesine geri döner.

# Uygulama

Genel olarak, yeni türler bu fonksiyonu yerine [`<`](@ref) uygulamalıdır ve geri dönüş tanımına `>(x, y) = y < x` dayanmalıdır.

# Örnekler

```jldoctest
julia> 'a' > 'b'
false

julia> 7 > 3 > 1
true

julia> "abc" > "abd"
false

julia> 5 > 3
true
```
