```
cumprod(A; dims::Integer)
```

Boyut `dim` boyunca kümülatif çarpım. Önceden tahsis edilmiş bir çıktı dizisi kullanmak için [`cumprod!`](@ref) ile de bakabilirsiniz, bu hem performans hem de çıktının hassasiyetini kontrol etmek için (örneğin taşmayı önlemek için) faydalıdır.

# Örnekler

```jldoctest
julia> a = Int8[1 2 3; 4 5 6];

julia> cumprod(a, dims=1)
2×3 Matrix{Int64}:
 1   2   3
 4  10  18

julia> cumprod(a, dims=2)
2×3 Matrix{Int64}:
 1   2    6
 4  20  120
```
