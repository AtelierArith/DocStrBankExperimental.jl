```
UnitRange{T<:Real}
```

`start`와 `stop`의 타입 `T`로 매개변수화된 범위로, `start`에서 시작하여 `stop`을 초과할 때까지 `1` 간격으로 요소로 채워집니다. `a:b` 구문에서 `a`와 `b`가 모두 `Integer`인 경우 `UnitRange`가 생성됩니다.

# 예제

```jldoctest
julia> collect(UnitRange(2.3, 5.2))
3-element Vector{Float64}:
 2.3
 3.3
 4.3

julia> typeof(1:10)
UnitRange{Int64}
```
