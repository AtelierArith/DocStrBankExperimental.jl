```
dayabbr(dt::TimeType; locale="korean") -> String
dayabbr(day::Integer; locale="korean") -> String
```

주어진 `locale`에 해당하는 요일의 약어 이름을 반환합니다. `Date` 또는 `DateTime`에 대해 사용할 수 있으며, `Integer`도 허용됩니다.

# 예시

```jldoctest
julia> dayabbr(Date("2000-01-01"))
"토"

julia> dayabbr(3)
"수"
```
