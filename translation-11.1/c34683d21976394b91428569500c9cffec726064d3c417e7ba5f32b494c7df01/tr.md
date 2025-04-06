```
any!(r, A)
```

`A` içindeki herhangi bir değerin `r`'nin tekil boyutları boyunca `true` olup olmadığını test eder ve sonuçları `r`'ye yazar.

!!! uyarı     Herhangi bir değiştirilmiş argümanın, başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.

# Örnekler

```jldoctest
julia> A = [true false; true false]
2×2 Matrix{Bool}:
 1  0
 1  0

julia> any!([1; 1], A)
2-element Vector{Int64}:
 1
 1

julia> any!([1 1], A)
1×2 Matrix{Int64}:
 1  0
```
