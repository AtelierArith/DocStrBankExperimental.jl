```
keepat!(a::Vector, inds)
keepat!(a::BitVector, inds)
```

Verilen `inds` tarafından belirtilmeyen tüm indekslerdeki öğeleri kaldırın ve değiştirilmiş `a`'yı döndürün. Korunan öğeler, sonuçta oluşan boşlukları doldurmak için kaydırılır.

!!! uyarı     Herhangi bir değiştirilmiş argümanın başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.

`inds`, sıralı ve benzersiz tam sayı indekslerinin bir yineleyicisi olmalıdır. Ayrıca bkz. [`deleteat!`](@ref).

!!! uyumluluk "Julia 1.7"
    Bu fonksiyon Julia 1.7 itibarıyla mevcuttur.


# Örnekler

```jldoctest
julia> keepat!([6, 5, 4, 3, 2, 1], 1:2:5)
3-element Vector{Int64}:
 6
 4
 2
```
