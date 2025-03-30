```
all!(r, A)
```

`A` içindeki tüm değerlerin `r`'nin tekil boyutları boyunca `true` olup olmadığını test eder ve sonuçları `r`'ye yazar.

!!! warning
    Herhangi bir değiştirilmiş argümanın başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.


# Örnekler

```jldoctest
julia> A = [true false; true false]
2×2 Matrix{Bool}:
 1  0
 1  0

julia> all!([1; 1], A)
2-element Vector{Int64}:
 0
 0

julia> all!([1 1], A)
1×2 Matrix{Int64}:
 1  0
```
