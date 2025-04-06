```
extrema!(r, A)
```

`A`'nın `r`'nin tekil boyutları üzerindeki minimum ve maksimum değerini hesaplayın ve sonuçları `r`'ye yazın.

!!! uyarı     Herhangi bir değiştirilmiş argümanın başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.

!!! uyumluluk "Julia 1.8"
    Bu yöntem Julia 1.8 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> extrema!([(1, 1); (1, 1)], A)
2-element Vector{Tuple{Int64, Int64}}:
 (1, 2)
 (3, 4)

julia> extrema!([(1, 1);; (1, 1)], A)
1×2 Matrix{Tuple{Int64, Int64}}:
 (1, 3)  (2, 4)
```
