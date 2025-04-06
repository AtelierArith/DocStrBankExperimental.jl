```
mean(f, A::AbstractArray; dims)
```

Dizi `A`'nın her bir elemanına `f` fonksiyonunu uygula ve `dims` boyutları üzerinde ortalamayı al.

!!! uyumluluk "Julia 1.3"
    Bu yöntem en az Julia 1.3 gerektirir.


```jldoctest
julia> using Statistics

julia> mean(√, [1, 2, 3])
1.3820881233139908

julia> mean([√1, √2, √3])
1.3820881233139908

julia> mean(√, [1 2 3; 4 5 6], dims=2)
2×1 Matrix{Float64}:
 1.3820881233139908
 2.2285192400943226
```
