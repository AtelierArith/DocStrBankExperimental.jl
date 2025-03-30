```
pop!(koleksiyon) -> öğe
```

`koleksiyon` içinden bir öğe çıkarır ve onu döndürür. Eğer `koleksiyon` sıralı bir konteyner ise, son öğe döndürülür; sırasız konteynerler için ise rastgele bir öğe döndürülür.

Ayrıca bakınız: [`popfirst!`](@ref), [`popat!`](@ref), [`delete!`](@ref), [`deleteat!`](@ref), [`splice!`](@ref), ve [`push!`](@ref).

# Örnekler

```jldoctest
julia> A=[1, 2, 3]
3-element Vector{Int64}:
 1
 2
 3

julia> pop!(A)
3

julia> A
2-element Vector{Int64}:
 1
 2

julia> S = Set([1, 2])
Set{Int64} with 2 elements:
  2
  1

julia> pop!(S)
2

julia> S
Set{Int64} with 1 element:
  1

julia> pop!(Dict(1=>2))
1 => 2
```
