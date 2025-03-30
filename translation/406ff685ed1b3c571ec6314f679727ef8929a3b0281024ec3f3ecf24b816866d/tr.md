```
CartesianIndex(i, j, k...)   -> I
CartesianIndex((i, j, k...)) -> I
```

Çok boyutlu bir indeks `I` oluşturun; bu, çok boyutlu bir dizi `A` için indeksleme yapmak üzere kullanılabilir. Özellikle, `A[I]` ifadesi `A[i,j,k...]` ile eşdeğerdir. Tam sayılar ve `CartesianIndex` indekslerini serbestçe karıştırabilirsiniz; örneğin, `A[Ipre, i, Ipost]` (burada `Ipre` ve `Ipost` `CartesianIndex` indeksleri ve `i` bir `Int`'dir) bir dizinin tek bir boyutunda çalışan algoritmalar yazarken yararlı bir ifade olabilir.

Bir `CartesianIndex`, bazen [`eachindex`](@ref) ile üretilir ve her zaman açık bir [`CartesianIndices`](@ref) ile yineleme yapıldığında üretilir.

Bir `I::CartesianIndex`, `broadcast` için bir "skalar" (bir konteyner değil) olarak işlenir. Bir `CartesianIndex`'in bileşenleri üzerinde yineleme yapmak için, `Tuple(I)` ile bir tuple'a dönüştürün.

# Örnekler

```jldoctest
julia> A = reshape(Vector(1:16), (2, 2, 2, 2))
2×2×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  3
 2  4

[:, :, 2, 1] =
 5  7
 6  8

[:, :, 1, 2] =
  9  11
 10  12

[:, :, 2, 2] =
 13  15
 14  16

julia> A[CartesianIndex((1, 1, 1, 1))]
1

julia> A[CartesianIndex((1, 1, 1, 2))]
9

julia> A[CartesianIndex((1, 1, 2, 1))]
5
```

!!! compat "Julia 1.10"
    `broadcast` için bir "skalar" olarak `CartesianIndex` kullanmak Julia 1.10'u gerektirir; önceki sürümlerde, `Ref(I)` kullanın.

