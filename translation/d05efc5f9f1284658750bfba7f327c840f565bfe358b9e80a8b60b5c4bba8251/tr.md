```
argmin(itr)
```

Bir koleksiyondaki en küçük elemanın indeksini veya anahtarını döndürür. Eğer birden fazla en küçük eleman varsa, ilk olanı döndürülür.

Koleksiyon boş olmamalıdır.

İndeksler, [`keys(itr)`](@ref) ve [`pairs(itr)`](@ref) tarafından döndürülenlerle aynı türdedir.

`NaN`, `missing` hariç tüm diğer değerlerden daha küçük olarak kabul edilir.

Ayrıca bakınız: [`argmax`](@ref), [`findmin`](@ref).

# Örnekler

```jldoctest
julia> argmin([8, 0.1, -9, pi])
3

julia> argmin([7, 1, 1, 6])
2

julia> argmin([7, 1, 1, NaN])
4
```
