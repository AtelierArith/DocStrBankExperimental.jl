```
empty!(collection) -> collection
```

`collection`의 모든 요소를 제거합니다.

# 예제

```jldoctest
julia> A = Dict("a" => 1, "b" => 2)
Dict{String, Int64} with 2 entries:
  "b" => 2
  "a" => 1

julia> empty!(A);

julia> A
Dict{String, Int64}()
```
