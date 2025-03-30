```
argmax(A; dims) -> indices
```

Bir dizi girişi için, verilen boyutlar üzerindeki maksimum elemanların indekslerini döndürün. `NaN`, diğer tüm değerlerden (istisna: `missing`) daha büyük olarak kabul edilir.

# Örnekler

```jldoctest
julia> A = [1.0 2; 3 4]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> argmax(A, dims=1)
1×2 Matrix{CartesianIndex{2}}:
 CartesianIndex(2, 1)  CartesianIndex(2, 2)

julia> argmax(A, dims=2)
2×1 Matrix{CartesianIndex{2}}:
 CartesianIndex(1, 2)
 CartesianIndex(2, 2)
```
