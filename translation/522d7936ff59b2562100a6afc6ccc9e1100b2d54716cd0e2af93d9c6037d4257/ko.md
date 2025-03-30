```
accumulate(op, A; dims::Integer, [init])
```

누적 연산 `op`를 `A`의 차원 `dims`를 따라 수행합니다 (벡터의 경우 `dims`는 선택적입니다). 초기값 `init`은 키워드 인수로 선택적으로 제공될 수 있습니다. 성능을 위해 미리 할당된 출력 배열을 사용하고 출력의 정밀도를 제어하기 위해 [`accumulate!`](@ref)도 참조하십시오 (예: 오버플로우를 피하기 위해).

일반적인 연산에 대해서는 `accumulate`의 특수화된 변형이 있습니다. [`cumsum`](@ref), [`cumprod`](@ref)를 참조하십시오. 지연 버전은 [`Iterators.accumulate`](@ref)를 참조하십시오.

!!! compat "Julia 1.5"
    비배열 반복자에서의 `accumulate`는 최소한 Julia 1.5가 필요합니다.


# 예제

```jldoctest
julia> accumulate(+, [1,2,3])
3-element Vector{Int64}:
 1
 3
 6

julia> accumulate(min, (1, -2, 3, -4, 5), init=0)
(0, -2, -2, -4, -4)

julia> accumulate(/, (2, 4, Inf), init=100)
(50.0, 12.5, 0.0)

julia> accumulate(=>, i^2 for i in 1:3)
3-element Vector{Any}:
          1
        1 => 4
 (1 => 4) => 9

julia> accumulate(+, fill(1, 3, 4))
3×4 Matrix{Int64}:
 1  4  7  10
 2  5  8  11
 3  6  9  12

julia> accumulate(+, fill(1, 2, 5), dims=2, init=100.0)
2×5 Matrix{Float64}:
 101.0  102.0  103.0  104.0  105.0
 101.0  102.0  103.0  104.0  105.0
```
