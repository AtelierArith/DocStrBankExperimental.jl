```
allunique(itr) -> Bool
allunique(f, itr) -> Bool
```

`itr`'den tüm değerlerin [`isequal`](@ref) ile karşılaştırıldığında farklı olması durumunda `true` döner. İkinci yöntem için ise `[f(x) for x in itr]`'nin tüm elemanlarının farklı olması durumunda `true` döner.

`allunique(f, itr)`'nin `length(itr)` kadar çağrılmayabileceğini unutmayın. Çağrıların kesin sayısı bir uygulama detayı olarak kabul edilir.

`allunique`, girdi sıralı olduğunda özel bir uygulama kullanabilir.

Ayrıca bakınız: [`unique`](@ref), [`issorted`](@ref), [`allequal`](@ref).

!!! uyumluluk "Julia 1.11"
    `allunique(f, itr)` yöntemi en az Julia 1.11 gerektirir.


# Örnekler

```jldoctest
julia> allunique([1, 2, 3])
true

julia> allunique([1, 2, 1, 2])
false

julia> allunique(Real[1, 1.0, 2])
false

julia> allunique([NaN, 2.0, NaN, 4.0])
false

julia> allunique(abs, [1, -1, 2])
false
```
