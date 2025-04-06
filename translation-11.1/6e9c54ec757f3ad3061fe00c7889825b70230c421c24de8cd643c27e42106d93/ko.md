```
firstdayofweek(dt::TimeType) -> TimeType
```

`dt`를 해당 주의 월요일로 조정합니다.

# 예시

```jldoctest
julia> firstdayofweek(DateTime("1996-01-05T12:30:00"))
1996-01-01T00:00:00
```
