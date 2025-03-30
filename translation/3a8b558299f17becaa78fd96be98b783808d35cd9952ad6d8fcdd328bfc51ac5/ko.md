```
repeat(A::AbstractArray; inner=ntuple(Returns(1), ndims(A)), outer=ntuple(Returns(1), ndims(A)))
```

`A`의 항목을 반복하여 배열을 구성합니다. `inner`의 i번째 요소는 `A`의 i번째 차원의 개별 항목이 반복되어야 하는 횟수를 지정합니다. `outer`의 i번째 요소는 `A`의 i번째 차원을 따라 슬라이스가 반복되어야 하는 횟수를 지정합니다. `inner` 또는 `outer`가 생략되면 반복이 수행되지 않습니다.

# 예제

```jldoctest
julia> repeat(1:2, inner=2)
4-element Vector{Int64}:
 1
 1
 2
 2

julia> repeat(1:2, outer=2)
4-element Vector{Int64}:
 1
 2
 1
 2

julia> repeat([1 2; 3 4], inner=(2, 1), outer=(1, 3))
4×6 Matrix{Int64}:
 1  2  1  2  1  2
 1  2  1  2  1  2
 3  4  3  4  3  4
 3  4  3  4  3  4
```
