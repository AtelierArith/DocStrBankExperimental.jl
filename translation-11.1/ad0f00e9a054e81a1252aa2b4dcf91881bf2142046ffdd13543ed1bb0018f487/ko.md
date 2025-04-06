```
isdiag(A) -> Bool
```

행렬이 대각선인지 테스트합니다. `iszero(A[i,j])`가 `i == j`가 아닌 경우에 참인 경우입니다. `A`가 정사각형일 필요는 없으며, 정사각형인지도 확인하고 싶다면 `size(A, 1) == size(A, 2)`를 확인해야 합니다.

# 예제

```jldoctest
julia> a = [1 2; 2 -1]
2×2 Matrix{Int64}:
 1   2
 2  -1

julia> isdiag(a)
false

julia> b = [im 0; 0 -im]
2×2 Matrix{Complex{Int64}}:
 0+1im  0+0im
 0+0im  0-1im

julia> isdiag(b)
true

julia> c = [1 0 0; 0 2 0]
2×3 Matrix{Int64}:
 1  0  0
 0  2  0

julia> isdiag(c)
true

julia> d = [1 0 0; 0 2 3]
2×3 Matrix{Int64}:
 1  0  0
 0  2  3

julia> isdiag(d)
false
```
