```
keys(a::AbstractArray)
```

`a` için şekline göre düzenlenmiş tüm geçerli indeksleri tanımlayan verimli bir dizi döndürür.

1 boyutlu dizilerin (vektörlerin) anahtarları tam sayılardır, oysa diğer N boyutlu diziler [`CartesianIndex`](@ref) kullanarak konumlarını tanımlar. Genellikle, bu tam sayı ve `CartesianIndex` dizilerini verimli bir şekilde temsil etmek için özel dizi türleri olan [`LinearIndices`](@ref) ve [`CartesianIndices`](@ref) kullanılır.

Bir dizinin `keys`'inin en verimli indeks türü olmayabileceğini unutmayın; maksimum performans için [`eachindex`](@ref) kullanın.

# Örnekler

```jldoctest
julia> keys([4, 5, 6])
3-element LinearIndices{1, Tuple{Base.OneTo{Int64}}}:
 1
 2
 3

julia> keys([4 5; 6 7])
CartesianIndices((2, 2))
```
