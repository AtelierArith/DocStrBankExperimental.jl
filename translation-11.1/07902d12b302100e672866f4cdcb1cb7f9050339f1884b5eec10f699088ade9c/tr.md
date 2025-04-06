```
findmin(itr) -> (x, index)
```

Koleksiyon `itr`'nin en küçük elemanını ve indeksini veya anahtarını döndürür. Eğer birden fazla en küçük eleman varsa, ilk olanı döndürülür. `NaN`, `missing` hariç tüm diğer değerlerden daha küçük olarak kabul edilir.

İndeksler, [`keys(itr)`](@ref) ve [`pairs(itr)`](@ref) tarafından döndürülenlerle aynı türdedir.

Ayrıca bakınız: [`findmax`](@ref), [`argmin`](@ref), [`minimum`](@ref).

# Örnekler

```jldoctest
julia> findmin([8, 0.1, -9, pi])
(-9.0, 3)

julia> findmin([1, 7, 7, 6])
(1, 1)

julia> findmin([1, 7, 7, NaN])
(NaN, 4)
```
