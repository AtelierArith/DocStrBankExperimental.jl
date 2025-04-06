```
rot180(A, k)
```

행렬 `A`를 180도 정수 `k`번 회전합니다. `k`가 짝수인 경우, 이는 `copy`와 동일합니다.

# 예제

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> rot180(a,1)
2×2 Matrix{Int64}:
 4  3
 2  1

julia> rot180(a,2)
2×2 Matrix{Int64}:
 1  2
 3  4
```
