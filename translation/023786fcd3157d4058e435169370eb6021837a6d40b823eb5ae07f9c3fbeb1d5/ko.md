```
^(b::Number, A::AbstractMatrix)
```

행렬 지수, $\exp(\log(b)A)$와 동등합니다.

!!! compat "Julia 1.1"
    `Irrational` 숫자(예: `ℯ`)를 행렬로 올리는 지원이 Julia 1.1에 추가되었습니다.


# 예제

```jldoctest
julia> 2^[1 2; 0 3]
2×2 Matrix{Float64}:
 2.0  6.0
 0.0  8.0

julia> ℯ^[1 2; 0 3]
2×2 Matrix{Float64}:
 2.71828  17.3673
 0.0      20.0855
```
