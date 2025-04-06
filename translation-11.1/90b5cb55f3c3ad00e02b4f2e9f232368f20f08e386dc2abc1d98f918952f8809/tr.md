```
minimum!(r, A)
```

`A`'nın `r`'nin tekil boyutları üzerindeki minimum değerini hesaplayın ve sonuçları `r`'ye yazın.

!!! uyarı     Herhangi bir değiştirilmiş argümanın başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.

# Örnekler

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> minimum!([1; 1], A)
2-element Vector{Int64}:
 1
 3

julia> minimum!([1 1], A)
1×2 Matrix{Int64}:
 1  2
```
