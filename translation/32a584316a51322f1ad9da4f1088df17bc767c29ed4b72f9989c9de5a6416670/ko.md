```
get!(collection, key, default)
```

주어진 키에 대해 저장된 값을 반환하거나, 키에 대한 매핑이 없으면 `key => default`를 저장하고 `default`를 반환합니다.

# 예제

```jldoctest
julia> d = Dict("a"=>1, "b"=>2, "c"=>3);

julia> get!(d, "a", 5)
1

julia> get!(d, "d", 4)
4

julia> d
Dict{String, Int64} with 4 entries:
  "c" => 3
  "b" => 2
  "a" => 1
  "d" => 4
```
