```
BoundsError([a],[i])
```

배열 `a`에 대한 인덱싱 작업이 인덱스 `i`에서 범위를 벗어난 요소에 접근하려고 시도했습니다.

# 예제

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> A = fill(1.0, 7);

julia> A[8]
ERROR: BoundsError: attempt to access 7-element Vector{Float64} at index [8]


julia> B = fill(1.0, (2,3));

julia> B[2, 4]
ERROR: BoundsError: attempt to access 2×3 Matrix{Float64} at index [2, 4]


julia> B[9]
ERROR: BoundsError: attempt to access 2×3 Matrix{Float64} at index [9]

```
