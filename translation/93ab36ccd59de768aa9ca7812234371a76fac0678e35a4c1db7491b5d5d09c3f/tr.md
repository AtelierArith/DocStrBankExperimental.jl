```
isapprox(x, y; atol::Real=0, rtol::Real=atol>0 ? 0 : √eps, nans::Bool=false[, norm::Function])
```

Kesin olmayan eşitlik karşılaştırması. İki sayı, göreceli mesafeleri *veya* mutlak mesafeleri tolerans sınırları içinde ise eşit kabul edilir: `isapprox`, `norm(x-y) <= max(atol, rtol*max(norm(x), norm(y)))` koşulu sağlandığında `true` döner. Varsayılan `atol` (mutlak tolerans) sıfırdır ve varsayılan `rtol` (göreceli tolerans) `x` ve `y`'nin türlerine bağlıdır. `nans` anahtar argümanı, NaN değerlerinin eşit kabul edilip edilmediğini belirler (varsayılan olarak false).

Gerçek veya karmaşık kayan nokta değerleri için, `atol > 0` belirtilmemişse, `rtol`, `x` veya `y` türlerinin en büyüğünün [`eps`](@ref) kareköküne varsayılan olarak ayarlanır (en az hassas). Bu, yaklaşık olarak yarım anlamlı basamağın eşitliğini gerektirir. Aksi takdirde, örneğin tam sayı argümanları için veya `atol > 0` sağlanmışsa, `rtol` varsayılan olarak sıfırdır.

`norm` anahtar kelimesi, sayısal `(x,y)` için `abs` ve diziler için `LinearAlgebra.norm` olarak varsayılan ayarlanmıştır (alternatif bir `norm` seçeneği bazen faydalı olabilir). `x` ve `y` diziler olduğunda, `norm(x-y)` sonlu değilse (yani `±Inf` veya `NaN`), karşılaştırma, `x` ve `y`'nin tüm elemanlarının bileşen bazında yaklaşık eşit olup olmadığını kontrol etmeye geri döner.

İkili operatör `≈`, varsayılan argümanlarla `isapprox` ile eşdeğerdir ve `x ≉ y`, `!isapprox(x,y)` ile eşdeğerdir.

`x ≈ 0` (yani, varsayılan toleranslarla sıfıra karşılaştırma) `x == 0` ile eşdeğerdir çünkü varsayılan `atol` sıfırdır. Bu tür durumlarda, uygun bir `atol` sağlamalı (veya `norm(x) ≤ atol` kullanmalısınız) veya kodunuzu yeniden düzenlemelisiniz (örneğin, `x ≈ y` kullanmak yerine `x - y ≈ 0` kullanın). Sıfırdan farklı bir `atol` otomatik olarak seçmek mümkün değildir çünkü bu, probleminizin genel ölçeklenmesine (birimlerine) bağlıdır: örneğin, `x - y ≈ 0` durumunda, `atol=1e-9`, `x` [Dünya'nın yarıçapı](https://en.wikipedia.org/wiki/Earth_radius) metre cinsinden ise son derece küçük bir tolerans, ancak `x` [Hidrojen atomunun yarıçapı](https://en.wikipedia.org/wiki/Bohr_radius) metre cinsinden ise son derece büyük bir tolerans olur.

!!! compat "Julia 1.6"
    Sayısal (dizi olmayan) argümanları karşılaştırırken `norm` anahtar argümanını geçmek, Julia 1.6 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> isapprox(0.1, 0.15; atol=0.05)
true

julia> isapprox(0.1, 0.15; rtol=0.34)
true

julia> isapprox(0.1, 0.15; rtol=0.33)
false

julia> 0.1 + 1e-10 ≈ 0.1
true

julia> 1e-10 ≈ 0
false

julia> isapprox(1e-10, 0, atol=1e-8)
true

julia> isapprox([10.0^9, 1.0], [10.0^9, 2.0]) # using `norm`
true
```
