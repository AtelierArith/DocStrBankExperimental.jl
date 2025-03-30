```
sort!(v; alg::Algorithm=defalg(v), lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

Vektörü `v` yerinde sıralar. Varsayılan olarak kararlı bir algoritma kullanılır: eşit karşılaştırılan elemanların sıralaması korunur. Belirli bir algoritma `alg` anahtar kelimesi aracılığıyla seçilebilir (mevcut algoritmalar için [Sıralama Algoritmaları](@ref) bölümüne bakın).

Elemanlar önce `by` fonksiyonu ile dönüştürülür ve ardından ya `lt` fonksiyonu ya da `order` sıralamasına göre karşılaştırılır. Son olarak, sonuç sıralaması `rev=true` ise tersine çevrilir (bu, ileri stabiliteyi korur: eşit karşılaştırılan elemanlar tersine çevrilmez). Mevcut uygulama, her karşılaştırmadan önce `by` dönüşümünü uygular, her eleman için bir kez değil.

`isless` dışındaki bir `lt` fonksiyonu ile [`Base.Order.Forward`](@ref) veya [`Base.Order.Reverse`](@ref) dışındaki bir `order` kullanmak yasaktır, aksi takdirde tüm seçenekler bağımsızdır ve tüm olası kombinasyonlarda birlikte kullanılabilir. `order` ayrıca bir "by" dönüşümü de içerebilir; bu durumda, `by` anahtar kelimesi ile tanımlanan dönüşümden sonra uygulanır. `order` değerleri hakkında daha fazla bilgi için [Alternatif Sıralamalar](@ref) belgesine bakın.

İki eleman arasındaki ilişkiler aşağıdaki gibi tanımlanır (bu durumda "daha az" ve "daha fazla" `rev=true` olduğunda değiştirilir):

  * `x`, `y`'den daha azdır eğer `lt(by(x), by(y))` (veya `Base.Order.lt(order, by(x), by(y))`) doğruysa.
  * `x`, `y`'den daha fazladır eğer `y`, `x`'den daha azdır.
  * `x` ve `y` eşdeğerdir eğer hiçbiri diğerinden daha az değildir ("karşılaştırılamaz" bazen "eşdeğer" için bir eşanlamlı olarak kullanılır).

`sort!` fonksiyonunun sonucu, her elemanın bir öncekinden daha büyük veya eşdeğer olduğu anlamında sıralıdır.

`lt` fonksiyonu katı bir zayıf sıralama tanımlamalıdır, yani:

  * irrefleksif olmalıdır: `lt(x, x)` her zaman `false` döner,
  * asimetrik olmalıdır: eğer `lt(x, y)` doğruysa, o zaman `lt(y, x)` yanlış olmalıdır,
  * geçişli olmalıdır: `lt(x, y) && lt(y, z)` ise `lt(x, z)`'yi gerektirir,
  * eşdeğerlikte geçişli olmalıdır: `!lt(x, y) && !lt(y, x)` ve `!lt(y, z) && !lt(z, y)` birlikte `!lt(x, z) && !lt(z, x)`'yi gerektirir. Kısacası: eğer `x` ve `y` eşdeğer ve `y` ve `z` eşdeğer ise, o zaman `x` ve `z` de eşdeğer olmalıdır.

Örneğin, `<` `Int` değerleri için geçerli bir `lt` fonksiyonudur, ancak `≤` değildir: irrefleksifliği ihlal eder. `Float64` değerleri için, `<` bile geçerli değildir çünkü dördüncü koşulu ihlal eder: `1.0` ve `NaN` eşdeğerdir ve `NaN` ve `2.0` da öyle, ancak `1.0` ve `2.0` eşdeğer değildir.

Ayrıca [`sort`](@ref), [`sortperm`](@ref), [`sortslices`](@ref), [`partialsort!`](@ref), [`partialsortperm`](@ref), [`issorted`](@ref), [`searchsorted`](@ref), [`insorted`](@ref), [`Base.Order.ord`](@ref) belgelerine de bakın.

# Örnekler

```jldoctest
julia> v = [3, 1, 2]; sort!(v); v
3-element Vector{Int64}:
 1
 2
 3

julia> v = [3, 1, 2]; sort!(v, rev = true); v
3-element Vector{Int64}:
 3
 2
 1

julia> v = [(1, "c"), (3, "a"), (2, "b")]; sort!(v, by = x -> x[1]); v
3-element Vector{Tuple{Int64, String}}:
 (1, "c")
 (2, "b")
 (3, "a")

julia> v = [(1, "c"), (3, "a"), (2, "b")]; sort!(v, by = x -> x[2]); v
3-element Vector{Tuple{Int64, String}}:
 (3, "a")
 (2, "b")
 (1, "c")

julia> sort(0:3, by=x->x-2, order=Base.Order.By(abs)) # same as sort(0:3, by=abs(x->x-2))
4-element Vector{Int64}:
 2
 1
 3
 0

julia> sort([2, NaN, 1, NaN, 3]) # correct sort with default lt=isless
5-element Vector{Float64}:
   1.0
   2.0
   3.0
 NaN
 NaN

julia> sort([2, NaN, 1, NaN, 3], lt=<) # wrong sort due to invalid lt. This behavior is undefined.
5-element Vector{Float64}:
   2.0
 NaN
   1.0
 NaN
   3.0
```
