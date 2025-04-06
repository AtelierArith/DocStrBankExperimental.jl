```
filter!(f, d::AbstractDict)
```

업데이트 `d`, `f`가 `false`인 요소를 제거합니다. 함수 `f`는 `key=>value` 쌍을 전달받습니다.

# 예제

```jldoctest
julia> d = Dict(1=>"a", 2=>"b", 3=>"c")
Dict{Int64, String} with 3 entries:
  2 => "b"
  3 => "c"
  1 => "a"

julia> filter!(p->isodd(p.first), d)
Dict{Int64, String} with 2 entries:
  3 => "c"
  1 => "a"
```
