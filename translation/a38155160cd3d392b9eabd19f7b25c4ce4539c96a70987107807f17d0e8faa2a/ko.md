```
diagm(v::AbstractVector)
diagm(m::Integer, n::Integer, v::AbstractVector)
```

벡터의 요소를 대각선 요소로 갖는 행렬을 생성합니다. 기본적으로 행렬은 정사각형이며 크기는 `length(v)`로 주어지지만, 비정사각형 크기 `m`×`n`는 첫 번째 인수로 `m,n`을 전달하여 지정할 수 있습니다.

# 예제

```jldoctest
julia> diagm([1,2,3])
3×3 Matrix{Int64}:
 1  0  0
 0  2  0
 0  0  3
```
