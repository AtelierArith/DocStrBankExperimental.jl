```
stride1(A) -> Int
```

배열 요소 간의 거리를 요소 크기 단위로 차원 1에서 반환합니다.

# 예시

```jldoctest
julia> A = [1,2,3,4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> LinearAlgebra.stride1(A)
1

julia> B = view(A, 2:2:4)
2-element view(::Vector{Int64}, 2:2:4) with eltype Int64:
 2
 4

julia> LinearAlgebra.stride1(B)
2
```
