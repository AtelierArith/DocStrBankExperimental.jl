```
lastdayofquarter(dt::TimeType) -> TimeType
```

`dt`를 해당 분기의 마지막 날로 조정합니다.

# 예시

```jldoctest
julia> lastdayofquarter(DateTime("1996-05-20"))
1996-06-30T00:00:00

julia> lastdayofquarter(DateTime("1996-08-20"))
1996-09-30T00:00:00
```
