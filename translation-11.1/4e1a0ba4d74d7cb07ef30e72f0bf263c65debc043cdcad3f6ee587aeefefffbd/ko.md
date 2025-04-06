```
ntuple(f, n::Integer)
```

길이 `n`의 튜플을 생성하며, 각 요소는 `f(i)`로 계산됩니다. 여기서 `i`는 요소의 인덱스입니다.

# 예제

```jldoctest
julia> ntuple(i -> 2*i, 4)
(2, 4, 6, 8)
```
