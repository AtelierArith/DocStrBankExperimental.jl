```
cumsum(itr)
```

이터레이터의 누적 합.

`+` 이외의 함수를 적용하려면 [`accumulate`](@ref)를 참조하세요.

!!! compat "Julia 1.5"
    비배열 이터레이터에서 `cumsum`을 사용하려면 최소한 Julia 1.5가 필요합니다.


# 예제

```jldoctest
julia> cumsum(1:3)
3-element Vector{Int64}:
 1
 3
 6

julia> cumsum((true, false, true, false, true))
(1, 1, 2, 2, 3)

julia> cumsum(fill(1, 2) for i in 1:3)
3-element Vector{Vector{Int64}}:
 [1, 1]
 [2, 2]
 [3, 3]
```
