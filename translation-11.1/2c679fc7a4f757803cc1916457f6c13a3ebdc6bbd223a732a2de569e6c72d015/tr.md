```
deleteat!(a::Vector, inds)
```

Verilen `inds` tarafından belirtilen indekslerdeki öğeleri kaldırır ve değiştirilmiş `a`'yı döndürür. Sonraki öğeler, oluşan boşluğu doldurmak için kaydırılır.

`inds`, ya bir yineleyici ya da sıralı ve benzersiz tam sayı indekslerinden oluşan bir koleksiyon ya da `a` ile aynı uzunlukta ve `true` değerinin silinecek girişleri gösterdiği bir boolean vektörü olabilir.

# Örnekler

```jldoctest
julia> deleteat!([6, 5, 4, 3, 2, 1], 1:2:5)
3-element Vector{Int64}:
 5
 3
 1

julia> deleteat!([6, 5, 4, 3, 2, 1], [true, false, true, false, true, false])
3-element Vector{Int64}:
 5
 3
 1

julia> deleteat!([6, 5, 4, 3, 2, 1], (2, 2))
HATA: ArgumentError: indeksler benzersiz ve sıralı olmalıdır
Stacktrace:
[...]
```
