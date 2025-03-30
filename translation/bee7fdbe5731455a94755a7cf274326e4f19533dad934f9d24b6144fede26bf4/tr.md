```
searchsortedlast(v, x; by=identity, lt=isless, rev=false)
```

`x`'den sonra sıralanmamış olan `v`'deki son değerin indeksini döndürür. Eğer `v`'deki tüm değerler `x`'den sonra sıralanmışsa, `firstindex(v) - 1` döner.

`v` vektörü, anahtar kelimeler tarafından tanımlanan sıraya göre sıralanmış olmalıdır. Döndürülen indeksin hemen sonrasına `x` eklemek, sıralı düzeni koruyacaktır. Anahtar kelimelerin anlamı ve kullanımı için [`sort!`](@ref) kısmına bakın. `by` fonksiyonu, aranan değer `x` ile `v`'deki değerlere uygulanır.

İndeks genellikle ikili arama kullanılarak bulunur, ancak bazı girdiler için optimize edilmiş uygulamalar vardır.

# Örnekler

```jldoctest
julia> searchsortedlast([1, 2, 4, 5, 5, 7], 4) # tek eşleşme
3

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 5) # birden fazla eşleşme
5

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 3) # eşleşme yok, ortada ekle
2

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 9) # eşleşme yok, sona ekle
6

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 0) # eşleşme yok, başa ekle
0

julia> searchsortedlast([1=>"bir", 2=>"iki", 4=>"dört"], 3=>"üç", by=first) # çiftlerin anahtarlarını karşılaştır
2
```
