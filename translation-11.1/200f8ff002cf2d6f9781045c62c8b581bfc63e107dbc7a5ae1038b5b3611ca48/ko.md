```
eigmin(A; permute::Bool=true, scale::Bool=true)
```

`A`의 가장 작은 고유값을 반환합니다. 옵션 `permute=true`는 행렬을 상삼각형에 더 가깝게 만들기 위해 행렬을 재배열하고, `scale=true`는 행렬의 대각선 요소로 행렬을 스케일링하여 행과 열의 노름을 더 비슷하게 만듭니다. `A`의 고유값이 복소수인 경우 이 방법은 실패합니다. 복소수는 정렬할 수 없기 때문입니다.

# 예제

```jldoctest
julia> A = [0 im; -im 0]
2×2 Matrix{Complex{Int64}}:
 0+0im  0+1im
 0-1im  0+0im

julia> eigmin(A)
-1.0

julia> A = [0 im; -1 0]
2×2 Matrix{Complex{Int64}}:
  0+0im  0+1im
 -1+0im  0+0im

julia> eigmin(A)
ERROR: DomainError with Complex{Int64}[0+0im 0+1im; -1+0im 0+0im]:
`A`는 복소수 고유값을 가질 수 없습니다.
Stacktrace:
[...]
```
