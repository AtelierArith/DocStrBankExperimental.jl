```
pairs(collection)
```

`key => value` 쌍에 대한 반복자를 반환합니다. 이는 키 집합을 값 집합에 매핑하는 모든 컬렉션에 해당합니다. 여기에는 배열이 포함되며, 배열의 키는 배열 인덱스입니다. 항목이 해시 테이블에 내부적으로 저장되는 경우, 예를 들어 `Dict`의 경우, 반환되는 순서는 달라질 수 있습니다. 그러나 `keys(a)`, `values(a)` 및 `pairs(a)`는 모두 `a`를 반복하고 동일한 순서로 요소를 반환합니다.

# 예제

```jldoctest
julia> a = Dict(zip(["a", "b", "c"], [1, 2, 3]))
Dict{String, Int64} with 3 entries:
  "c" => 3
  "b" => 2
  "a" => 1

julia> pairs(a)
Dict{String, Int64} with 3 entries:
  "c" => 3
  "b" => 2
  "a" => 1

julia> foreach(println, pairs(["a", "b", "c"]))
1 => "a"
2 => "b"
3 => "c"

julia> (;a=1, b=2, c=3) |> pairs |> collect
3-element Vector{Pair{Symbol, Int64}}:
 :a => 1
 :b => 2
 :c => 3

julia> (;a=1, b=2, c=3) |> collect
3-element Vector{Int64}:
 1
 2
 3
```
