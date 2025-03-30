```
argmax(itr)
```

Bir koleksiyondaki en büyük elemanın indeksini veya anahtarını döndürür. Eğer birden fazla en büyük eleman varsa, ilk olanı döndürülür.

Koleksiyon boş olmamalıdır.

İndeksler, [`keys(itr)`](@ref) ve [`pairs(itr)`](@ref) tarafından döndürülenlerle aynı türdendir.

Değerler `isless` ile karşılaştırılır.

Ayrıca bakınız: [`argmin`](@ref), [`findmax`](@ref).

# Örnekler

```jldoctest
julia> argmax([8, 0.1, -9, pi])
1

julia> argmax([1, 7, 7, 6])
2

julia> argmax([1, 7, 7, NaN])
4
```
