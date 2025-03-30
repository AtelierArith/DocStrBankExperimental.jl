```
replace!(new::Union{Function, Type}, A; [count::Integer])
```

컬렉션 `A`의 각 요소 `x`를 `new(x)`로 교체합니다. `count`가 지정된 경우, 총 `count` 값만큼 최대한 교체합니다(교체는 `new(x) !== x`로 정의됨).

# 예제

```jldoctest
julia> replace!(x -> isodd(x) ? 2x : x, [1, 2, 3, 4])
4-element Vector{Int64}:
 2
 2
 6
 4

julia> replace!(Dict(1=>2, 3=>4)) do kv
           first(kv) < 3 ? first(kv)=>3 : kv
       end
Dict{Int64, Int64} with 2 entries:
  3 => 4
  1 => 3

julia> replace!(x->2x, Set([3, 6]))
Set{Int64} with 2 elements:
  6
  12
```
