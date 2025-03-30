```
firstdayofmonth(dt::TimeType) -> TimeType
```

`dt`를 해당 월의 첫 번째 날로 조정합니다.

# 예시

```jldoctest
julia> firstdayofmonth(DateTime("1996-05-20"))
1996-05-01T00:00:00
```
