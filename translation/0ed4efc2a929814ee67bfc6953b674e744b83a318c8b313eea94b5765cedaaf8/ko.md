```
map!(f, values(dict::AbstractDict))
```

`dict`를 수정하여 각 값을 `val`에서 `f(val)`로 변환합니다. `dict`의 타입은 변경할 수 없음을 유의하세요: 만약 `f(val)`이 `dict`의 값 타입의 인스턴스가 아니라면, 가능할 경우 값 타입으로 변환되며, 그렇지 않으면 오류가 발생합니다.

!!! compat "Julia 1.2"
    `map!(f, values(dict::AbstractDict))`는 Julia 1.2 이상이 필요합니다.


# 예제

```jldoctest
julia> d = Dict(:a => 1, :b => 2)
Dict{Symbol, Int64} with 2 entries:
  :a => 1
  :b => 2

julia> map!(v -> v-1, values(d))
ValueIterator for a Dict{Symbol, Int64} with 2 entries. Values:
  0
  1
```
