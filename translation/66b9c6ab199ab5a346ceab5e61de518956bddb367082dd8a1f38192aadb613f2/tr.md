```
eigvals(A; permute::Bool=true, scale::Bool=true, sortby) -> values
```

`A`'nın özdeğerlerini döndürür.

Genel simetrik olmayan matrisler için, özdeğer hesaplamasından önce matrisin nasıl dengeleneceğini belirtmek mümkündür. `permute`, `scale` ve `sortby` anahtar kelimeleri, [`eigen`](@ref) için olanlarla aynıdır.

# Örnekler

```jldoctest
julia> diag_matrix = [1 0; 0 4]
2×2 Matrix{Int64}:
 1  0
 0  4

julia> eigvals(diag_matrix)
2-element Vector{Float64}:
 1.0
 4.0
```
