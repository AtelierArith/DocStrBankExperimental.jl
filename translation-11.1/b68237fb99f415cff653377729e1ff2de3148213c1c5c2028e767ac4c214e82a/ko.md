```
mean!(r, v)
```

`v`의 평균을 `r`의 단일 차원에 대해 계산하고 결과를 `r`에 기록합니다.

# 예제

```jldoctest
julia> using Statistics

julia> v = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> mean!([1., 1.], v)
2-element Vector{Float64}:
 1.5
 3.5

julia> mean!([1. 1.], v)
1×2 Matrix{Float64}:
 2.0  3.0
```
