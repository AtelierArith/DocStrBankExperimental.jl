```
mean(f, itr)
```

Koleksiyon `itr`'nin her bir elemanına `f` fonksiyonunu uygula ve ortalamasını al.

```jldoctest
julia> using Statistics

julia> mean(√, [1, 2, 3])
1.3820881233139908

julia> mean([√1, √2, √3])
1.3820881233139908
```
