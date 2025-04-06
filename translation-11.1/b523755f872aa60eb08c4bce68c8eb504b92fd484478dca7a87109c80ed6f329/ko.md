```
rotr90(A)
```

행렬 `A`를 오른쪽으로 90도 회전시킵니다.

# 예시

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> rotr90(a)
2×2 Matrix{Int64}:
 3  1
 4  2
```
