```
nextind(A, i)
```

`i`'den sonra `A`'da bulunan indeksi döndürür. Döndürülen indeks genellikle bir tam sayı `i` için `i + 1` ile eşdeğerdir. Bu fonksiyon, genel kodlar için yararlı olabilir.

!!! warning
    Döndürülen indeks sınırların dışında olabilir. [`checkbounds`](@ref) kullanmayı düşünün.


Ayrıca bakınız: [`prevind`](@ref).

# Örnekler

```jldoctest
julia> x = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> nextind(x, 1) # geçerli sonuç
2

julia> nextind(x, 4) # geçersiz sonuç
5

julia> nextind(x, CartesianIndex(1, 1)) # geçerli sonuç
CartesianIndex(2, 1)

julia> nextind(x, CartesianIndex(2, 2)) # geçersiz sonuç
CartesianIndex(1, 3)
```
