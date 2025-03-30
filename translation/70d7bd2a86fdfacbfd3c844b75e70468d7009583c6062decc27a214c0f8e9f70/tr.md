```
prevind(A, i)
```

`A` içindeki `i`'den önceki indeksi döndürür. Döndürülen indeks genellikle bir tamsayı `i` için `i - 1` ile eşdeğerdir. Bu fonksiyon, genel kod için yararlı olabilir.

!!! warning
    Döndürülen indeks sınırların dışında olabilir. [`checkbounds`](@ref) kullanmayı düşünün.


Ayrıca bakınız: [`nextind`](@ref).

# Örnekler

```jldoctest
julia> x = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> prevind(x, 4) # geçerli sonuç
3

julia> prevind(x, 1) # geçersiz sonuç
0

julia> prevind(x, CartesianIndex(2, 2)) # geçerli sonuç
CartesianIndex(1, 2)

julia> prevind(x, CartesianIndex(1, 1)) # geçersiz sonuç
CartesianIndex(2, 0)
```
