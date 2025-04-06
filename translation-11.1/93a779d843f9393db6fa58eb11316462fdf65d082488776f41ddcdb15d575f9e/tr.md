```
lastindex(koleksiyon) -> Tam Sayı
lastindex(koleksiyon, d) -> Tam Sayı
```

`koleksiyon`'un son indeksini döndürür. Eğer `d` verilmişse, `koleksiyon`'un `d` boyutundaki son indeksini döndürür.

`A[end]` ve `A[end, end]` sözdizimleri sırasıyla `A[lastindex(A)]` ve `A[lastindex(A, 1), lastindex(A, 2)]`'ye dönüşür.

Ayrıca bkz: [`axes`](@ref), [`firstindex`](@ref), [`eachindex`](@ref), [`prevind`](@ref).

# Örnekler

```jldoctest
julia> lastindex([1,2,4])
3

julia> lastindex(rand(3,4,5), 2)
4
```
