```
hvcat(blocks_per_row::Union{Tuple{Vararg{Int}}, Int}, values...)
```

Tek bir çağrıda yatay ve dikey birleştirme. Bu fonksiyon blok matris sözdizimi için çağrılır. İlk argüman, her blok satırında birleştirilecek argüman sayısını belirtir. İlk argüman tek bir tamsayı `n` ise, tüm blok satırlarının `n` blok sütuna sahip olduğu varsayılır.

# Örnekler

```jldoctest
julia> a, b, c, d, e, f = 1, 2, 3, 4, 5, 6
(1, 2, 3, 4, 5, 6)

julia> [a b c; d e f]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> hvcat((3,3), a,b,c,d,e,f)
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> [a b; c d; e f]
3×2 Matrix{Int64}:
 1  2
 3  4
 5  6

julia> hvcat((2,2,2), a,b,c,d,e,f)
3×2 Matrix{Int64}:
 1  2
 3  4
 5  6
julia> hvcat((2,2,2), a,b,c,d,e,f) == hvcat(2, a,b,c,d,e,f)
true
```
