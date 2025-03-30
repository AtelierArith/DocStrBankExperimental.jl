```
isless(x, y)
```

`x`'in `y`'den küçük olup olmadığını, sabit bir toplam sıralama ([`isequal`](@ref) ile birlikte tanımlanmış) açısından test eder. `isless`, tüm türlerin `(x, y)` çiftleri için tanımlı değildir. Ancak, tanımlıysa, aşağıdaki koşulları sağlaması beklenir:

  * Eğer `isless(x, y)` tanımlıysa, o zaman `isless(y, x)` ve `isequal(x, y)` de tanımlıdır ve bu üçünden tam olarak biri `true` döner.
  * `isless` ile tanımlanan ilişki geçişkendir, yani `isless(x, y) && isless(y, z)` ise `isless(x, z)`'yi gerektirir.

Normalde sıralanmamış olan değerler, örneğin `NaN`, normal değerlere göre sıralanır. [`missing`](@ref) değerleri en sona sıralanır.

Bu, [`sort!`](@ref) tarafından kullanılan varsayılan karşılaştırmadır.

# Uygulama

Toplam sıralaması olan sayısal olmayan türler bu işlevi uygulamalıdır. Sayısal türler yalnızca `NaN` gibi özel değerlere sahipse bunu uygulamak zorundadır. Kısmi sıralaması olan türler [`<`](@ref) uygulamalıdır. Sıralama ve ilgili işlevlerde kullanılabilecek alternatif sıralama yöntemlerini tanımlamak için [Alternatif Sıralamalar](@ref) belgesine bakın.

# Örnekler

```jldoctest
julia> isless(1, 3)
true

julia> isless("Red", "Blue")
false
```
