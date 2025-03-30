```
resize!(a::Vector, n::Integer) -> Vector
```

`a`를 `n` 요소를 포함하도록 크기를 조정합니다. `n`이 현재 컬렉션 길이보다 작으면 처음 `n` 요소가 유지됩니다. `n`이 더 크면 새로운 요소가 초기화될 것이라고 보장되지 않습니다.

# 예제

```jldoctest
julia> resize!([6, 5, 4, 3, 2, 1], 3)
3-element Vector{Int64}:
 6
 5
 4

julia> a = resize!([6, 5, 4, 3, 2, 1], 8);

julia> length(a)
8

julia> a[1:6]
6-element Vector{Int64}:
 6
 5
 4
 3
 2
 1
```
