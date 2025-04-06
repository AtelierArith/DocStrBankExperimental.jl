```
findmin(f, A; dims) -> (f(x), index)
```

Dizi girişi için, verilen boyutlar üzerinde `f`'yi minimize eden karşılık gelen değerin kodomainedeki değerini ve indeksini döndürür.

# Örnekler

```jldoctest
julia> A = [-1.0 1; -0.5 2]
2×2 Matrix{Float64}:
 -1.0  1.0
 -0.5  2.0

julia> findmin(abs2, A, dims=1)
([0.25 1.0], CartesianIndex{2}[CartesianIndex(2, 1) CartesianIndex(1, 2)])

julia> findmin(abs2, A, dims=2)
([1.0; 0.25;;], CartesianIndex{2}[CartesianIndex(1, 1); CartesianIndex(2, 1);;])
```
