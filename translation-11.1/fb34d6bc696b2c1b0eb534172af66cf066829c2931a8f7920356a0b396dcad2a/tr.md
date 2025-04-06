```
eachindex(A...)
eachindex(::IndexStyle, A::AbstractArray...)
```

Bir `AbstractArray` `A`'nın her indeksini verimli bir şekilde ziyaret etmek için bir yineleyici nesne oluşturur. Hızlı lineer indekslemeye (örneğin `Array` gibi) katılan dizi türleri için bu, 1 tabanlı indeksleme kullanıyorlarsa basitçe `1:length(A)` aralığıdır. Hızlı lineer indekslemeye katılmayan dizi türleri için, genellikle her boyut için belirtilen indekslerle diziyi verimli bir şekilde indekslemek için özel bir Kartezyen aralığı döndürülür.

Genel olarak `eachindex`, dizeler ve sözlükler de dahil olmak üzere keyfi yineleyicileri kabul eder ve keyfi indeks türlerini (örneğin, düzensiz aralıklı veya tam sayı olmayan indeksler) destekleyen bir yineleyici nesnesi döndürür.

Eğer `A` bir `AbstractArray` ise, `eachindex`'in döndürmesi gereken indekslerin stilini açıkça belirtmek için ilk argüman olarak `IndexStyle` türünde bir değer geçerek belirtebilirsiniz (genellikle lineer indeksler gerekiyorsa `IndexLinear()`, Kartezyen aralık isteniyorsa `IndexCartesian()`).

Birden fazla `AbstractArray` argümanı sağlarsanız, `eachindex` tüm argümanlar için hızlı bir yineleyici nesnesi oluşturur (genellikle tüm girdilerin hızlı lineer indekslemesi varsa bir [`UnitRange`](@ref), aksi takdirde bir [`CartesianIndices`](@ref)). Eğer diziler farklı boyutlara ve/veya boyutlara sahipse, bir `DimensionMismatch` istisnası fırlatılacaktır.

Ayrıca, indeksler ve değerler üzerinde birlikte yineleme yapmak için [`pairs`](@ref)`(A)` ve bir boyut boyunca geçerli indeksler için [`axes`](@ref)`(A, 2)`'yi de görebilirsiniz.

# Örnekler

```jldoctest
julia> A = [10 20; 30 40];

julia> for i in eachindex(A) # lineer indeksleme
           println("A[", i, "] == ", A[i])
       end
A[1] == 10
A[2] == 30
A[3] == 20
A[4] == 40

julia> for i in eachindex(view(A, 1:2, 1:1)) # Kartezyen indeksleme
           println(i)
       end
CartesianIndex(1, 1)
CartesianIndex(2, 1)
```
