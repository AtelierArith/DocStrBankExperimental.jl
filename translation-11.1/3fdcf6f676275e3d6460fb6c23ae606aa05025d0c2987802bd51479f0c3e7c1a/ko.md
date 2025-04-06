```
rotl90(A, k)
```

행렬 `A`를 90도 반시계 방향으로 정수 `k`만큼 왼쪽으로 회전합니다. `k`가 4의 배수(0 포함)인 경우, 이는 `copy`와 동일합니다.

# 예제

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> rotl90(a,1)
2×2 Matrix{Int64}:
 2  4
 1  3

julia> rotl90(a,2)
2×2 Matrix{Int64}:
 4  3
 2  1

julia> rotl90(a,3)
2×2 Matrix{Int64}:
 3  1
 4  2

julia> rotl90(a,4)
2×2 Matrix{Int64}:
 1  2
 3  4
```
