```
mean(f, A::AbstractArray; dims)
```

함수 `f`를 배열 `A`의 각 요소에 적용하고 차원 `dims`에 대해 평균을 구합니다.

!!! compat "Julia 1.3"
    이 메서드는 최소한 Julia 1.3이 필요합니다.


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
