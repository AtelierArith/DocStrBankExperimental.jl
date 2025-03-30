```
cumprod(itr)
```

이터레이터의 누적 곱.

또한 [`cumprod!`](@ref), [`accumulate`](@ref), [`cumsum`](@ref)를 참조하세요.

!!! compat "Julia 1.5"
    비배열 이터레이터에서 `cumprod`는 최소한 Julia 1.5가 필요합니다.


# 예제

```jldoctest
julia> cumprod(fill(1//2, 3))
3-element Vector{Rational{Int64}}:
 1//2
 1//4
 1//8

julia> cumprod((1, 2, 1, 3, 1))
(1, 2, 2, 6, 6)

julia> cumprod("julia")
5-element Vector{String}:
 "j"
 "ju"
 "jul"
 "juli"
 "julia"
```
