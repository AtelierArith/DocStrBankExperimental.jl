```
lastdayofweek(dt::TimeType) -> TimeType
```

`dt`를 해당 주의 일요일로 조정합니다.

# 예시

```jldoctest
julia> lastdayofweek(DateTime("1996-01-05T12:30:00"))
1996-01-07T00:00:00
```
