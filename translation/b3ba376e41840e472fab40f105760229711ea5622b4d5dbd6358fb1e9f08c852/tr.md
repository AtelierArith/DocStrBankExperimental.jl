```
ord(lt, by, rev::Union{Bool, Nothing}, order::Ordering=Forward)
```

Aynı argümanlarla bir [`Ordering`](@ref) nesnesi oluşturun [`sort!`](@ref). Elemanlar önce `by` fonksiyonu (bu [`identity`](@ref) olabilir) ile dönüştürülür ve ardından ya `lt` fonksiyonu ya da mevcut bir sıralama `order` ile karşılaştırılır. `lt`, [`isless`](@ref) veya [`sort!`](@ref) `lt` parametresinin aynı kurallarına uyan bir fonksiyon olmalıdır. Son olarak, elde edilen sıralama `rev=true` ise tersine çevrilir.

`isless` dışındaki bir `lt` ile [`Base.Order.Forward`](@ref) veya [`Base.Order.Reverse`](@ref) dışındaki bir `order` geçmek yasaktır, aksi takdirde tüm seçenekler bağımsızdır ve tüm olası kombinasyonlarda birlikte kullanılabilir.
