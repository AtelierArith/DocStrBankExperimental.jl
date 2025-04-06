```
eigvecs(A; permute::Bool=true, scale::Bool=true, `sortby`) -> Matrix
```

`A`'nın özvektillerini içeren `M` matrisini döndürür. (`k`'nci özvektör `M[:, k]` diliminden elde edilebilir.) `permute`, `scale` ve `sortby` anahtar kelimeleri [`eigen`](@ref) ile aynıdır.

# Örnekler

```jldoctest
julia> eigvecs([1.0 0.0 0.0; 0.0 3.0 0.0; 0.0 0.0 18.0])
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0
```
