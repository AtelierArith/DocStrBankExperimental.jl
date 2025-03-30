```
drop(iter, n)
```

`iter`의 첫 번째 `n` 요소를 제외한 모든 요소를 생성하는 반복자입니다.

# 예제

```jldoctest
julia> a = 1:2:11
1:2:11

julia> collect(a)
6-element Vector{Int64}:
  1
  3
  5
  7
  9
 11

julia> collect(Iterators.drop(a,4))
2-element Vector{Int64}:
  9
 11
```
