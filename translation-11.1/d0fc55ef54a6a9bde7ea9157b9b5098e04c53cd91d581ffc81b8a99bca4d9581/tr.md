```
searchsorted(v, x; by=identity, lt=isless, rev=false)
```

`v` içinde `x` ile eşdeğer değerlere karşılık gelen indekslerin aralığını döndürür veya `v`'de `x` ile eşdeğer değerler yoksa ekleme noktasında bulunan boş bir aralık döndürür. `v` vektörü, anahtar kelimeler tarafından tanımlanan sıraya göre sıralanmış olmalıdır. Anahtar kelimelerin anlamı ve eşdeğerlik tanımı için [`sort!`](@ref) kısmına bakın. `by` fonksiyonu, aranan değer `x` ile `v` içindeki değerlere uygulanır.

Aralık genellikle ikili arama kullanılarak bulunur, ancak bazı girdiler için optimize edilmiş uygulamalar vardır.

Ayrıca bakınız: [`searchsortedfirst`](@ref), [`sort!`](@ref), [`insorted`](@ref), [`findall`](@ref).

# Örnekler

```jldoctest
julia> searchsorted([1, 2, 4, 5, 5, 7], 4) # tek eşleşme
3:3

julia> searchsorted([1, 2, 4, 5, 5, 7], 5) # birden fazla eşleşme
4:5

julia> searchsorted([1, 2, 4, 5, 5, 7], 3) # eşleşme yok, ortada ekle
3:2

julia> searchsorted([1, 2, 4, 5, 5, 7], 9) # eşleşme yok, sonunda ekle
7:6

julia> searchsorted([1, 2, 4, 5, 5, 7], 0) # eşleşme yok, başta ekle
1:0

julia> searchsorted([1=>"one", 2=>"two", 2=>"two", 4=>"four"], 2=>"two", by=first) # çiftlerin anahtarlarını karşılaştır
2:3
```
