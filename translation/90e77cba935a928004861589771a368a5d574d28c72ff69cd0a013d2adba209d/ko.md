```
haskey(collection, key) -> Bool
```

주어진 `key`에 대한 매핑이 컬렉션에 있는지 여부를 결정합니다.

# 예제

```jldoctest
julia> D = Dict('a'=>2, 'b'=>3)
Dict{Char, Int64} with 2 entries:
  'a' => 2
  'b' => 3

julia> haskey(D, 'a')
true

julia> haskey(D, 'c')
false
```
