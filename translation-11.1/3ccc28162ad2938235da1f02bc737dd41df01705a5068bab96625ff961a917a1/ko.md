```
firstdayofyear(dt::TimeType) -> TimeType
```

`dt`를 해당 연도의 첫 번째 날로 조정합니다.

# 예시

```jldoctest
julia> firstdayofyear(DateTime("1996-05-20"))
1996-01-01T00:00:00
```
