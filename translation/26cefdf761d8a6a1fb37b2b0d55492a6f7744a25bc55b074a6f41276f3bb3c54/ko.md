```
lastdayofyear(dt::TimeType) -> TimeType
```

`dt`를 해당 연도의 마지막 날로 조정합니다.

# 예시

```jldoctest
julia> lastdayofyear(DateTime("1996-05-20"))
1996-12-31T00:00:00
```
