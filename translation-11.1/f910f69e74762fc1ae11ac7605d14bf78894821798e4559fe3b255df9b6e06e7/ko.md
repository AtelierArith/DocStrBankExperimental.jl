```
issparse(S)
```

`S`가 희소 행렬이면 `true`를 반환하고, 그렇지 않으면 `false`를 반환합니다.

# 예제

```jldoctest
julia> sv = sparsevec([1, 4], [2.3, 2.2], 10)
10-element SparseVector{Float64, Int64} with 2 stored entries:
  [1]  =  2.3
  [4]  =  2.2

julia> issparse(sv)
true

julia> issparse(Array(sv))
false
```
