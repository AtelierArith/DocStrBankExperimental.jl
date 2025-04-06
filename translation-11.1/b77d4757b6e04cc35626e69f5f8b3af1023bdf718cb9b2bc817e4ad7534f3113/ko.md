```
lastdayofmonth(dt::TimeType) -> TimeType
```

`dt`를 해당 월의 마지막 날로 조정합니다.

# 예제

```jldoctest
julia> lastdayofmonth(DateTime("1996-05-20"))
1996-05-31T00:00:00
```
