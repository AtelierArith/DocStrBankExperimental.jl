```
<(x, y)
```

Küçükten büyüğe karşılaştırma operatörü. [`isless`](@ref) fonksiyonuna geri döner. Kayar nokta NaN değerlerinin davranışı nedeniyle, bu operatör kısmi bir sıralama uygular.

# Uygulama

Kanonik bir kısmi sıralamaya sahip yeni türler, bu fonksiyonu yeni türün iki argümanı için uygulamalıdır. Kanonik bir tam sıralamaya sahip türler ise [`isless`](@ref) fonksiyonunu uygulamalıdır.

Ayrıca bkz. [`isunordered`](@ref).

# Örnekler

```jldoctest
julia> 'a' < 'b'
true

julia> "abc" < "abd"
true

julia> 5 < 3
false
```
