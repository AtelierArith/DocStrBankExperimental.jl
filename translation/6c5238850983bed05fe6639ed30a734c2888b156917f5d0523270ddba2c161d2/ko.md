```
sparsevec(A)
```

벡터 `A`를 길이 `m`의 희소 벡터로 변환합니다.

# 예제

```jldoctest
julia> sparsevec([1.0, 2.0, 0.0, 0.0, 3.0, 0.0])
6-element SparseVector{Float64, Int64} with 3 stored entries:
  [1]  =  1.0
  [2]  =  2.0
  [5]  =  3.0
```
