```
findmax(f, A; dims) -> (f(x), index)
```

Bir dizi girişi için, verilen boyutlar üzerinde `f`'yi maksimize eden karşılık gelen değerin kodomandaki değerini ve indeksini döndürür.

# Örnekler

```jldoctest
julia> A = [-1.0 1; -0.5 2]
2×2 Matrix{Float64}:
 -1.0  1.0
 -0.5  2.0

julia> findmax(abs2, A, dims=1)
([1.0 4.0], CartesianIndex{2}[CartesianIndex(1, 1) CartesianIndex(2, 2)])

julia> findmax(abs2, A, dims=2)
([1.0; 4.0;;], CartesianIndex{2}[CartesianIndex(1, 1); CartesianIndex(2, 2);;])
```
