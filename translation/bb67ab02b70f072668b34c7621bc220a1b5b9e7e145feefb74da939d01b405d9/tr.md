```
allequal(itr) -> Bool
allequal(f, itr) -> Bool
```

`itr`'den alınan tüm değerler [`isequal`](@ref) ile karşılaştırıldığında eşitse `true` döner. İkinci yöntem içinse, `[f(x) for x in itr]`'nin tüm elemanları eşitse.

`allequal(f, itr)`'nin `f`'yi `length(itr)` kadar çağırmayabileceğini unutmayın. Çağrıların kesin sayısı bir uygulama detayı olarak kabul edilir.

Ayrıca bakınız: [`unique`](@ref), [`allunique`](@ref).

!!! uyumluluk "Julia 1.8"
    `allequal` fonksiyonu en az Julia 1.8 gerektirir.


!!! uyumluluk "Julia 1.11"
    `allequal(f, itr)` metodu en az Julia 1.11 gerektirir.


# Örnekler

```jldoctest
julia> allequal([])
true

julia> allequal([1])
true

julia> allequal([1, 1])
true

julia> allequal([1, 2])
false

julia> allequal(Dict(:a => 1, :b => 1))
false

julia> allequal(abs2, [1, -1])
true
```
