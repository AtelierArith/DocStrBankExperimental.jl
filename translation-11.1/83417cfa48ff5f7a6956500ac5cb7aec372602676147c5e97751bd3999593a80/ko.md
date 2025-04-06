```
LinearAlgebra.checksquare(A)
```

행렬이 정사각형인지 확인한 다음, 공통 차원을 반환합니다. 여러 인수가 있는 경우 벡터를 반환합니다.

# 예제

```jldoctest
julia> A = fill(1, (4,4)); B = fill(1, (5,5));

julia> LinearAlgebra.checksquare(A, B)
2-element Vector{Int64}:
 4
 5
```
