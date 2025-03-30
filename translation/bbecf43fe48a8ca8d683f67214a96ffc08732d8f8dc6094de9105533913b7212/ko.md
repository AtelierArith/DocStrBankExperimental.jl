```
filter(f, d::AbstractDict)
```

`f`가 `false`인 요소를 제거하고 `d`의 복사본을 반환합니다. 함수 `f`는 `key=>value` 쌍을 전달받습니다.

# 예제

```jldoctest
julia> d = Dict(1=>"a", 2=>"b")
Dict{Int64, String} with 2 entries:
  2 => "b"
  1 => "a"

julia> filter(p->isodd(p.first), d)
Dict{Int64, String} with 1 entry:
  1 => "a"
```
