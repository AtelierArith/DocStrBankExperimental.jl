```
firstindex(koleksiyon) -> Tam Sayı
firstindex(koleksiyon, d) -> Tam Sayı
```

`koleksiyon`'un ilk indeksini döndürür. Eğer `d` verilmişse, `koleksiyon`'un `d` boyutundaki ilk indeksini döndürür.

`A[begin]` ve `A[1, begin]` sözdizimleri sırasıyla `A[firstindex(A)]` ve `A[1, firstindex(A, 2)]`'ye dönüşür.

Ayrıca bakınız: [`first`](@ref), [`axes`](@ref), [`lastindex`](@ref), [`nextind`](@ref).

# Örnekler

```jldoctest
julia> firstindex([1,2,4])
1

julia> firstindex(rand(3,4,5), 2)
1
```
