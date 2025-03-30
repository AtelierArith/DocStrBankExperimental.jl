```
getindex(A, inds...)
```

Dizi `A`'nın, `inds` indeksleriyle seçilen bir alt kümesini döndürür.

Her bir indeks, [`Integer`](@ref), [`CartesianIndex`](@ref), [aralık](@ref Base.AbstractRange) veya desteklenen indekslerin [dizisi](@ref man-multi-dim-arrays) gibi herhangi bir [desteklenen indeks türü](@ref man-supported-index-types) olabilir. Belirli bir boyutta tüm elemanları seçmek için bir [:](@ref Base.Colon) kullanılabilir ve karşılık gelen indeksin `true` olduğu elemanları filtrelemek için bir boolean dizisi (örneğin, bir `Array{Bool}` veya bir [`BitArray`](@ref)) kullanılabilir.

`inds` birden fazla eleman seçtiğinde, bu fonksiyon yeni bir dizi döndürür. Kopya oluşturmadan birden fazla elemanı indekslemek için [`view`](@ref) kullanın.

Ayrıntılar için [dizi indeksleme](@ref man-array-indexing) bölümüne bakın.

# Örnekler

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> getindex(A, 1)
1

julia> getindex(A, [2, 1])
2-element Vector{Int64}:
 3
 1

julia> getindex(A, 2:4)
3-element Vector{Int64}:
 3
 2
 4

julia> getindex(A, 2, 1)
3

julia> getindex(A, CartesianIndex(2, 1))
3

julia> getindex(A, :, 2)
2-element Vector{Int64}:
 2
 4

julia> getindex(A, 2, :)
2-element Vector{Int64}:
 3
 4

julia> getindex(A, A .> 2)
2-element Vector{Int64}:
 3
 4
```
