```
rotl90(A)
```

행렬 `A`를 왼쪽으로 90도 회전시킵니다.

# 예제

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> rotl90(a)
2×2 Matrix{Int64}:
 2  4
 1  3
```
