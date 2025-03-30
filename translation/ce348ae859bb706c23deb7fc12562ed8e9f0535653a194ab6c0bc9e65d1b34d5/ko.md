```
istriu(A::AbstractMatrix, k::Integer = 0) -> Bool
```

`A`가 `k`번째 초대각선에서 시작하는 상삼각행렬인지 테스트합니다.

# 예시

```jldoctest
julia> a = [1 2; 2 -1]
2×2 Matrix{Int64}:
 1   2
 2  -1

julia> istriu(a)
false

julia> istriu(a, -1)
true

julia> c = [1 1 1; 1 1 1; 0 1 1]
3×3 Matrix{Int64}:
 1  1  1
 1  1  1
 0  1  1

julia> istriu(c)
false

julia> istriu(c, -1)
true
```
