```
stride(A, k::Integer)
```

차원 `k`에서 인접한 요소 간의 메모리 거리(요소 수)를 반환합니다.

참고: [`strides`](@ref).

# 예제

```jldoctest
julia> A = fill(1, (3,4,5));

julia> stride(A,2)
3

julia> stride(A,3)
12
```
