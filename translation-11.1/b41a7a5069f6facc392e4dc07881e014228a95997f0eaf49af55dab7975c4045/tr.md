```
union(s, itrs...)
∪(s, itrs...)
```

Tüm argümanlardan tüm farklı öğeleri içeren bir nesne oluşturur.

İlk argüman, hangi türde bir konteyner döndürüleceğini kontrol eder. Eğer bu bir dizi ise, öğelerin ilk göründüğü sırayı korur.

Unicode `∪`, Julia REPL'de `\cup` yazıp ardından tab tuşuna basarak ve birçok editörde yazılabilir. Bu, `s ∪ itr` şeklinde kullanılan bir infiks operatördür.

Ayrıca [`unique`](@ref), [`intersect`](@ref), [`isdisjoint`](@ref), [`vcat`](@ref), [`Iterators.flatten`](@ref) ile de ilgili.

# Örnekler

```jldoctest
julia> union([1, 2], [3])
3-element Vector{Int64}:
 1
 2
 3

julia> union([4 2 3 4 4], 1:3, 3.0)
4-element Vector{Float64}:
 4.0
 2.0
 3.0
 1.0

julia> (0, 0.0) ∪ (-0.0, NaN)
3-element Vector{Real}:
   0
  -0.0
 NaN

julia> union(Set([1, 2]), 2:3)
Set{Int64} with 3 elements:
  2
  3
  1
```
