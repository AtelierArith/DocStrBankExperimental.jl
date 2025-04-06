```
values(a::AbstractDict)
```

모음의 모든 값에 대한 반복자를 반환합니다. `collect(values(a))`는 값의 배열을 반환합니다. 값이 해시 테이블에 내부적으로 저장될 때, `Dict`의 경우와 같이 반환되는 순서는 달라질 수 있습니다. 그러나 `keys(a)`, `values(a)` 및 `pairs(a)`는 모두 `a`를 반복하고 동일한 순서로 요소를 반환합니다.

# 예제

```jldoctest
julia> D = Dict('a'=>2, 'b'=>3)
Dict{Char, Int64} with 2 entries:
  'a' => 2
  'b' => 3

julia> collect(values(D))
2-element Vector{Int64}:
 2
 3
```
