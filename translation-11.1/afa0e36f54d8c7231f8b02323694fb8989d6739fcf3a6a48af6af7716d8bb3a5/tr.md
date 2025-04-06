```
intersect(s, itrs...)
∩(s, itrs...)
```

Tüm argümanlarda bulunan öğeleri içeren küme oluşturur.

İlk argüman, hangi tür konteynerin döndürüleceğini kontrol eder. Eğer bu bir dizi ise, öğelerin ilk göründüğü sırayı korur.

Unicode `∩` Julia REPL'de `\cap` yazıp ardından tab tuşuna basarak ve birçok editörde yazılabilir. Bu, `s ∩ itr` şeklinde kullanılabilen bir infiks operatördür.

Ayrıca [`setdiff`](@ref), [`isdisjoint`](@ref), [`issubset`](@ref Base.issubset), [`issetequal`](@ref) ile de ilgili.

!!! compat "Julia 1.8"
    Julia 1.8 itibarıyla intersect, iki girişin tür-promote edilmiş eltype'lerinin eltype'ine sahip bir sonuç döndürür.


# Örnekler

```jldoctest
julia> intersect([1, 2, 3], [3, 4, 5])
1-element Vector{Int64}:
 3

julia> intersect([1, 4, 4, 5, 6], [6, 4, 6, 7, 8])
2-element Vector{Int64}:
 4
 6

julia> intersect(1:16, 7:99)
7:16

julia> (0, 0.0) ∩ (-0.0, 0)
1-element Vector{Real}:
 0

julia> intersect(Set([1, 2]), BitSet([2, 3]), 1.0:10.0)
Set{Float64} with 1 element:
  2.0
```
