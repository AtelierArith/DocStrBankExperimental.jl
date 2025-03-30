```
length(collection) -> Tam sayı
```

Koleksiyondaki eleman sayısını döndürür.

İndekslenebilir bir koleksiyonun son geçerli indeksini almak için [`lastindex`](@ref) kullanın.

Ayrıca bakınız: [`size`](@ref), [`ndims`](@ref), [`eachindex`](@ref).

# Örnekler

```jldoctest
julia> length(1:5)
5

julia> length([1, 2, 3, 4])
4

julia> length([1 2; 3 4])
4
```
