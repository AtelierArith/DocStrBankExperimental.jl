```
insorted(x, v; by=identity, lt=isless, rev=false) -> Bool
```

Bir vektör `v`'nin `x` ile eşdeğer herhangi bir değeri içerip içermediğini belirleyin. Vektör `v`, anahtar kelimeler tarafından tanımlanan sıraya göre sıralanmış olmalıdır. Anahtar kelimelerin anlamı ve eşdeğerlik tanımı için [`sort!`](@ref) belgesine bakın. `by` fonksiyonu, aranan değer `x` ile `v`'deki değerlere uygulanır.

Kontrol genellikle ikili arama kullanılarak yapılır, ancak bazı girdiler için optimize edilmiş uygulamalar vardır.

Ayrıca [`in`](@ref) belgesine bakın.

# Örnekler

```jldoctest
julia> insorted(4, [1, 2, 4, 5, 5, 7]) # tek eşleşme
true

julia> insorted(5, [1, 2, 4, 5, 5, 7]) # birden fazla eşleşme
true

julia> insorted(3, [1, 2, 4, 5, 5, 7]) # eşleşme yok
false

julia> insorted(9, [1, 2, 4, 5, 5, 7]) # eşleşme yok
false

julia> insorted(0, [1, 2, 4, 5, 5, 7]) # eşleşme yok
false

julia> insorted(2=>"TWO", [1=>"one", 2=>"two", 4=>"four"], by=first) # çiftlerin anahtarlarını karşılaştır
true
```

!!! compat "Julia 1.6"
    `insorted` Julia 1.6'da eklendi.

