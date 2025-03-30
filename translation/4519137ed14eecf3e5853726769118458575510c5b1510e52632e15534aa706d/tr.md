```
isequal(x, y) -> Bool
```

[`==`](@ref) ile benzer, ancak kayan nokta sayıları ve eksik değerlerin işlenmesi açısından farklılık gösterir. `isequal`, tüm kayan nokta `NaN` değerlerini birbirine eşit olarak kabul eder, `-0.0` değerini `0.0` değerine eşit olmayan olarak değerlendirir ve [`missing`](@ref) değerini `missing` ile eşit kabul eder. Her zaman bir `Bool` değeri döner.

`isequal`, bir eşitlik ilişkisi olup - reflexif ( `===` ifadesi `isequal`'ı ima eder), simetrik (`isequal(a, b)` ifadesi `isequal(b, a)`'yı ima eder) ve geçişli (`isequal(a, b)` ve `isequal(b, c)` ifadesi `isequal(a, c)`'yi ima eder).

# Uygulama

`isequal`'ın varsayılan uygulaması `==` çağrısı yapar, bu nedenle genellikle yalnızca `==` tanımlaması gereken bir tür, kayan nokta değerleri içermeyen bir türdür.

`isequal`, hash tabloları (`Dict`) tarafından kullanılan karşılaştırma fonksiyonudur. `isequal(x,y)` ifadesi, `hash(x) == hash(y)` ifadesini ima etmelidir.

Bu genellikle, özel bir `==` veya `isequal` yöntemi bulunan türlerin, karşılık gelen bir [`hash`](@ref) yöntemini uygulaması gerektiği anlamına gelir (ve tersine). Koleksiyonlar genellikle tüm içeriklerde `isequal`'ı özyinelemeli olarak çağırarak `isequal`'ı uygular.

Ayrıca, `isequal`, [`isless`](@ref) ile bağlantılıdır ve birlikte, tam bir sıralama tanımlamak için çalışırlar; burada `isequal(x, y)`, `isless(x, y)` veya `isless(y, x)` ifadelerinden tam olarak biri `true` olmalıdır (diğer ikisi `false`).

Skalar türler genellikle `==` ile ayrı bir `isequal` uygulamasına ihtiyaç duymaz, yalnızca daha verimli bir uygulama sağlayan kayan nokta sayılarını temsil ediyorlarsa ( `isnan`, `signbit` ve `==`'ya dayalı olarak sağlanan genel bir geri dönüş).

# Örnekler

```jldoctest
julia> isequal([1., NaN], [1., NaN])
true

julia> [1., NaN] == [1., NaN]
false

julia> 0.0 == -0.0
true

julia> isequal(0.0, -0.0)
false

julia> missing == missing
missing

julia> isequal(missing, missing)
true
```
