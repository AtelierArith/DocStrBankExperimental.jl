```
strides(A)
```

각 차원에서 메모리 스트라이드를 튜플로 반환합니다.

참고: [`stride`](@ref).

# 예제

```jldoctest
julia> A = fill(1, (3,4,5));

julia> strides(A)
(1, 3, 12)
```
