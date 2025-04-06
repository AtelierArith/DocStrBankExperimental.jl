```
firstdayofquarter(dt::TimeType) -> TimeType
```

`dt`를 해당 분기의 첫 번째 날로 조정합니다.

# 예시

```jldoctest
julia> firstdayofquarter(DateTime("1996-05-20"))
1996-04-01T00:00:00

julia> firstdayofquarter(DateTime("1996-08-20"))
1996-07-01T00:00:00
```
