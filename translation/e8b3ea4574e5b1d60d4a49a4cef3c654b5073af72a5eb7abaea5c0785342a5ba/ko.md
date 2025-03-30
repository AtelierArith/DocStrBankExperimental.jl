```
values(iterator)
```

키와 값이 있는 반복자 또는 컬렉션에 대해 값에 대한 반복자를 반환합니다. 이 함수는 기본적으로 인수를 그대로 반환합니다. 일반적인 반복자의 요소는 보통 "값"으로 간주되기 때문입니다.

# 예제

```jldoctest
julia> d = Dict("a"=>1, "b"=>2);

julia> values(d)
ValueIterator for a Dict{String, Int64} with 2 entries. Values:
  2
  1

julia> values([2])
1-element Vector{Int64}:
 2
```
