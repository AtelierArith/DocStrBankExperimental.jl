```
findall(A)
```

`A`'nın `true` indekslerini veya anahtarlarını içeren bir vektör `I` döndürür. Eğer `A`'da böyle bir eleman yoksa, boş bir dizi döndürülür. Diğer türdeki değerleri aramak için, ilk argüman olarak bir predikat geçirin.

İndeksler veya anahtarlar, [`keys(A)`](@ref) ve [`pairs(A)`](@ref) tarafından döndürülenlerle aynı türdedir.

Ayrıca bakınız: [`findfirst`](@ref), [`searchsorted`](@ref).

# Örnekler

```jldoctest
julia> A = [true, false, false, true]
4-element Vector{Bool}:
 1
 0
 0
 1

julia> findall(A)
2-element Vector{Int64}:
 1
 4

julia> A = [true false; false true]
2×2 Matrix{Bool}:
 1  0
 0  1

julia> findall(A)
2-element Vector{CartesianIndex{2}}:
 CartesianIndex(1, 1)
 CartesianIndex(2, 2)

julia> findall(falses(3))
Int64[]
```
