```
Dates.ISODateFormat
```

날짜에 대한 ISO8601 형식을 설명합니다. 이것은 `Date`의 `Dates.format`에 대한 기본값입니다.

# 예제

```jldoctest
julia> Dates.format(Date(2018, 8, 8), ISODateFormat)
"2018-08-08"
```
