```
Dict([itr])
```

`Dict{K,V}()`는 타입 `K`의 키와 타입 `V`의 값을 가진 해시 테이블을 생성합니다. 키는 [`isequal`](@ref)로 비교되고 [`hash`](@ref)로 해시됩니다.

단일 iterable 인수를 주면, 인수에 의해 생성된 2-튜플 `(key,value)`에서 키-값 쌍을 가져오는 [`Dict`](@ref)를 생성합니다.

# 예제

```jldoctest
julia> Dict([("A", 1), ("B", 2)])
Dict{String, Int64} with 2 entries:
  "B" => 2
  "A" => 1
```

대안으로, 쌍 인수의 시퀀스를 전달할 수 있습니다.

```jldoctest
julia> Dict("A"=>1, "B"=>2)
Dict{String, Int64} with 2 entries:
  "B" => 2
  "A" => 1
```

!!! 경고     키는 변경 가능하지만, 저장된 키를 변경하면 해시 테이블이 내부적으로 일관성이 없게 될 수 있으며, 이 경우 `Dict`가 제대로 작동하지 않습니다. 키를 변경해야 하는 경우 [`IdDict`](@ref)가 대안이 될 수 있습니다.
