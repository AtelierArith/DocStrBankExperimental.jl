```
searchsortedfirst(v, x; by=identity, lt=isless, rev=false)
```

`v` içindeki `x`'den önce sıralanmamış ilk değerin indeksini döndürür. Eğer `v` içindeki tüm değerler `x`'den önce sıralanmışsa, `lastindex(v) + 1` döner.

`v` vektörü, anahtar kelimeler tarafından tanımlanan sıraya göre sıralanmış olmalıdır. Döndürülen indekse `x` eklemek, sıralı düzeni koruyacaktır. Anahtar kelimelerin anlamı ve kullanımı için [`sort!`](@ref) kısmına bakın. `by` fonksiyonu, aranan değer `x` ile `v` içindeki değerlere uygulanır.

İndeks genellikle ikili arama kullanılarak bulunur, ancak bazı girdiler için optimize edilmiş uygulamalar vardır.

Ayrıca bakınız: [`searchsortedlast`](@ref), [`searchsorted`](@ref), [`findfirst`](@ref).

# Örnekler

```jldoctest
julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 4) # tek eşleşme
3

julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 5) # birden fazla eşleşme
4

julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 3) # eşleşme yok, ortada ekle
3

julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 9) # eşleşme yok, sona ekle
7

julia> searchsortedfirst([1, 2, 4, 5, 5, 7], 0) # eşleşme yok, başa ekle
1

julia> searchsortedfirst([1=>"one", 2=>"two", 4=>"four"], 3=>"three", by=first) # çiftlerin anahtarlarını karşılaştır
3
```
