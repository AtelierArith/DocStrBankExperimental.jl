```
sparsevec(I, V, [m, combine])
```

길이 `m`인 희소 벡터 `S`를 생성하여 `S[I[k]] = V[k]`가 되도록 합니다. 중복 항목은 `combine` 함수를 사용하여 결합되며, `combine` 인수가 제공되지 않으면 기본값은 `+`입니다. 단, `V`의 요소가 부울인 경우 `combine`의 기본값은 `|`입니다.

# 예제

```jldoctest
julia> II = [1, 3, 3, 5]; V = [0.1, 0.2, 0.3, 0.2];

julia> sparsevec(II, V)
5-element SparseVector{Float64, Int64} with 3 stored entries:
  [1]  =  0.1
  [3]  =  0.5
  [5]  =  0.2

julia> sparsevec(II, V, 8, -)
8-element SparseVector{Float64, Int64} with 3 stored entries:
  [1]  =  0.1
  [3]  =  -0.1
  [5]  =  0.2

julia> sparsevec([1, 3, 1, 2, 2], [true, true, false, false, false])
3-element SparseVector{Bool, Int64} with 3 stored entries:
  [1]  =  1
  [2]  =  0
  [3]  =  1
```
