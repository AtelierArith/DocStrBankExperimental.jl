```
monthname(dt::TimeType; locale="korean") -> String
monthname(month::Integer, locale="korean") -> String
```

주어진 `locale`에 따라 `Date` 또는 `DateTime` 또는 `Integer`의 월 이름을 반환합니다.

# 예시

```jldoctest
julia> monthname(Date("2005-01-04"))
"1월"

julia> monthname(2)
"2월"
```
