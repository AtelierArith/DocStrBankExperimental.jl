```
svdvals(A, B)
```

`A`와 `B`의 일반화된 특이값 분해에서 일반화된 특이값을 반환합니다. [`svd`](@ref)도 참조하십시오.

# 예제

```jldoctest
julia> A = [1. 0.; 0. -1.]
2×2 Matrix{Float64}:
 1.0   0.0
 0.0  -1.0

julia> B = [0. 1.; 1. 0.]
2×2 Matrix{Float64}:
 0.0  1.0
 1.0  0.0

julia> svdvals(A, B)
2-element Vector{Float64}:
 1.0
 1.0
```
