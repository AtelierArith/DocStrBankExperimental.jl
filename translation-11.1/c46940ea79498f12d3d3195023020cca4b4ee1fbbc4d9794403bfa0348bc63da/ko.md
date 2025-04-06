```
sortslices(A; dims, alg::Algorithm=DEFAULT_UNSTABLE, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

배열 `A`의 슬라이스를 정렬합니다. 필수 키워드 인수 `dims`는 정수 또는 정수의 튜플이어야 합니다. 이는 슬라이스가 정렬되는 차원(dimension)을 지정합니다.

예를 들어, `A`가 행렬인 경우, `dims=1`은 행을 정렬하고, `dims=2`는 열을 정렬합니다. 1차원 슬라이스에 대한 기본 비교 함수는 사전식으로 정렬합니다.

나머지 키워드 인수에 대한 내용은 [`sort!`](@ref) 문서를 참조하십시오.

# 예제

```jldoctest
julia> sortslices([7 3 5; -1 6 4; 9 -2 8], dims=1) # 행 정렬
3×3 Matrix{Int64}:
 -1   6  4
  7   3  5
  9  -2  8

julia> sortslices([7 3 5; -1 6 4; 9 -2 8], dims=1, lt=(x,y)->isless(x[2],y[2]))
3×3 Matrix{Int64}:
  9  -2  8
  7   3  5
 -1   6  4

julia> sortslices([7 3 5; -1 6 4; 9 -2 8], dims=1, rev=true)
3×3 Matrix{Int64}:
  9  -2  8
  7   3  5
 -1   6  4

julia> sortslices([7 3 5; 6 -1 -4; 9 -2 8], dims=2) # 열 정렬
3×3 Matrix{Int64}:
  3   5  7
 -1  -4  6
 -2   8  9

julia> sortslices([7 3 5; 6 -1 -4; 9 -2 8], dims=2, alg=InsertionSort, lt=(x,y)->isless(x[2],y[2]))
3×3 Matrix{Int64}:
  5   3  7
 -4  -1  6
  8  -2  9

julia> sortslices([7 3 5; 6 -1 -4; 9 -2 8], dims=2, rev=true)
3×3 Matrix{Int64}:
 7   5   3
 6  -4  -1
 9   8  -2
```

# 고차원

`sortslices`는 고차원으로 자연스럽게 확장됩니다. 예를 들어, `A`가 2x2x2 배열인 경우, `sortslices(A, dims=3)`는 3차원 내에서 슬라이스를 정렬하며, 2x2 슬라이스 `A[:, :, 1]`과 `A[:, :, 2]`를 비교 함수에 전달합니다. 고차원 슬라이스에는 기본 순서가 없지만, `by` 또는 `lt` 키워드 인수를 사용하여 그러한 순서를 지정할 수 있습니다.

`dims`가 튜플인 경우, `dims`의 차원 순서가 중요하며 슬라이스의 선형 순서를 지정합니다. 예를 들어, `A`가 3차원이고 `dims`가 `(1, 2)`인 경우, 첫 번째 두 차원의 순서가 재배열되어 나머지 세 번째 차원의 슬라이스가 정렬됩니다. 대신 `dims`가 `(2, 1)`인 경우, 동일한 슬라이스가 선택되지만 결과 순서는 행 우선(row-major)으로 변경됩니다.

# 고차원 예제

```
julia> A = [4 3; 2 1 ;;; 'A' 'B'; 'C' 'D']
2×2×2 Array{Any, 3}:
[:, :, 1] =
 4  3
 2  1

[:, :, 2] =
 'A'  'B'
 'C'  'D'

julia> sortslices(A, dims=(1,2))
2×2×2 Array{Any, 3}:
[:, :, 1] =
 1  3
 2  4

[:, :, 2] =
 'D'  'B'
 'C'  'A'

julia> sortslices(A, dims=(2,1))
2×2×2 Array{Any, 3}:
[:, :, 1] =
 1  2
 3  4

[:, :, 2] =
 'D'  'C'
 'B'  'A'

julia> sortslices(reshape([5; 4; 3; 2; 1], (1,1,5)), dims=3, by=x->x[1,1])
1×1×5 Array{Int64, 3}:
[:, :, 1] =
 1

[:, :, 2] =
 2

[:, :, 3] =
 3

[:, :, 4] =
 4

[:, :, 5] =
 5
```
