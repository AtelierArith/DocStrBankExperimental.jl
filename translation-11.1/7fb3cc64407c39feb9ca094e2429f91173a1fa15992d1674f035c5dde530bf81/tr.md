```
findmax(itr) -> (x, index)
```

Koleksiyon `itr`'nin en büyük elemanını ve indeksini veya anahtarını döndürür. Eğer birden fazla en büyük eleman varsa, ilk olanı döndürülür. Değerler `isless` ile karşılaştırılır.

İndeksler, [`keys(itr)`](@ref) ve [`pairs(itr)`](@ref) tarafından döndürülenlerle aynı türdendir.

Ayrıca bakınız: [`findmin`](@ref), [`argmax`](@ref), [`maximum`](@ref).

# Örnekler

```jldoctest
julia> findmax([8, 0.1, -9, pi])
(8.0, 1)

julia> findmax([1, 7, 7, 6])
(7, 2)

julia> findmax([1, 7, 7, NaN])
(NaN, 4)
```
