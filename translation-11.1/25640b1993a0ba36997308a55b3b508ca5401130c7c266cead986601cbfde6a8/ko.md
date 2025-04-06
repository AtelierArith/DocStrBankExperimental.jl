```
sparsevec(d::Dict, [m])
```

길이 `m`의 희소 벡터를 생성하며, 비영(非零) 인덱스는 사전의 키이고, 비영 값은 사전의 값입니다.

# 예제

```jldoctest
julia> sparsevec(Dict(1 => 3, 2 => 2))
2-element SparseVector{Int64, Int64} with 2 stored entries:
  [1]  =  3
  [2]  =  2
```
