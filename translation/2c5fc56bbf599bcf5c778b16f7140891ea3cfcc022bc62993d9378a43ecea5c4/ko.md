```
delete!(collection, key)
```

주어진 키에 대한 매핑을 컬렉션에서 삭제하고, 컬렉션을 반환합니다.

# 예제

```jldoctest
julia> d = Dict("a"=>1, "b"=>2)
Dict{String, Int64} with 2 entries:
  "b" => 2
  "a" => 1

julia> delete!(d, "b")
Dict{String, Int64} with 1 entry:
  "a" => 1

julia> delete!(d, "b") # d는 변경되지 않음
Dict{String, Int64} with 1 entry:
  "a" => 1
```
