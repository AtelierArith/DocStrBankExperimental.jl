```
spdiagm(v::AbstractVector)
spdiagm(m::Integer, n::Integer, v::AbstractVector)
```

벡터의 요소를 대각선 요소로 갖는 희소 행렬을 생성합니다. 기본적으로(`m`과 `n`이 주어지지 않은 경우) 행렬은 정사각형이며 크기는 `length(v)`로 주어지지만, `m`과 `n`을 첫 번째 인수로 전달하여 비정사각형 크기 `m`×`n`을 지정할 수 있습니다.

!!! compat "Julia 1.6"
    이 함수는 최소한 Julia 1.6이 필요합니다.


# 예제

```jldoctest
julia> spdiagm([1,2,3])
3×3 SparseMatrixCSC{Int64, Int64} with 3 stored entries:
 1  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  3

julia> spdiagm(sparse([1,0,3]))
3×3 SparseMatrixCSC{Int64, Int64} with 2 stored entries:
 1  ⋅  ⋅
 ⋅  ⋅  ⋅
 ⋅  ⋅  3
```
