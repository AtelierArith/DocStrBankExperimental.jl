```
prepend!(a::Vector, collections...) -> collection
```

각 `collections`의 요소를 `a`의 시작 부분에 삽입합니다.

`collections`가 여러 개의 컬렉션을 지정할 경우, 순서가 유지됩니다: `collections[1]`의 요소가 `a`의 가장 왼쪽에 나타나고, 그 다음으로 이어집니다.

!!! compat "Julia 1.6"
    여러 개의 컬렉션을 prepend하기 위해서는 최소한 Julia 1.6이 필요합니다.


# 예제

```jldoctest
julia> prepend!([3], [1, 2])
3-element Vector{Int64}:
 1
 2
 3

julia> prepend!([6], [1, 2], [3, 4, 5])
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```
