```
hvcat(blocks_per_row::Union{Tuple{Vararg{Int}}, Int}, values...)
```

한 번의 호출로 수평 및 수직 연결. 이 함수는 블록 행렬 구문에 대해 호출됩니다. 첫 번째 인수는 각 블록 행에서 연결할 인수의 수를 지정합니다. 첫 번째 인수가 단일 정수 `n`인 경우 모든 블록 행은 `n`개의 블록 열을 가진 것으로 간주됩니다.

# 예제

```jldoctest
julia> a, b, c, d, e, f = 1, 2, 3, 4, 5, 6
(1, 2, 3, 4, 5, 6)

julia> [a b c; d e f]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> hvcat((3,3), a,b,c,d,e,f)
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> [a b; c d; e f]
3×2 Matrix{Int64}:
 1  2
 3  4
 5  6

julia> hvcat((2,2,2), a,b,c,d,e,f)
3×2 Matrix{Int64}:
 1  2
 3  4
 5  6
julia> hvcat((2,2,2), a,b,c,d,e,f) == hvcat(2, a,b,c,d,e,f)
true
```
