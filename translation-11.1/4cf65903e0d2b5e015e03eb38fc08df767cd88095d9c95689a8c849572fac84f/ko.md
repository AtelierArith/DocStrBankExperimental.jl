```
Dates.ISODateTimeFormat
```

날짜와 시간에 대한 ISO8601 형식을 설명합니다. 이것은 `DateTime`의 `Dates.format`에 대한 기본값입니다.

# 예제

```jldoctest
julia> Dates.format(DateTime(2018, 8, 8, 12, 0, 43, 1), ISODateTimeFormat)
"2018-08-08T12:00:43.001"
```
