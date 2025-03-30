```
Base.split_rest(collection, n::Int[, itr_state]) -> (rest_but_n, last_n)
```

Belirli bir yineleme durumu `itr_state`'den başlayarak `collection`'ın kuyruğunu ayırmak için genel bir işlev. İki yeni koleksiyonun bir demetini döndürür. İlk koleksiyon, son `n` eleman hariç kuyruğun tüm elemanlarını içerirken, ikinci koleksiyonu oluşturur.

İlk koleksiyonun türü genellikle [`Base.rest`](@ref) türünü takip eder, ancak yedek durum tembel değildir, bunun yerine bir vektöre hevesle toplanır.

Kullanıcı tanımlı koleksiyon türleri için, `a, b..., c = collection` gibi son konumda [atama sırasında yutma](@ref destructuring-assignment) davranışını özelleştirmek için aşırı yüklenebilir.

!!! compat "Julia 1.9"
    `Base.split_rest`, en az Julia 1.9 gerektirir.


Ayrıca bakınız: [`Base.rest`](@ref).

# Örnekler

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> first, state = iterate(a)
(1, 2)

julia> first, Base.split_rest(a, 1, state)
(1, ([3, 2], [4]))
```
