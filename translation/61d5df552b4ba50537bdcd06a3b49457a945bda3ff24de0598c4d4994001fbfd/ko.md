```
dayname(dt::TimeType; locale="korean") -> String
dayname(day::Integer; locale="korean") -> String
```

주어진 `locale`에 따라 `Date` 또는 `DateTime`의 요일에 해당하는 전체 요일 이름을 반환합니다. `Integer`도 허용됩니다.

# 예시

```jldoctest
julia> dayname(Date("2000-01-01"))
"토요일"

julia> dayname(4)
"목요일"
```
