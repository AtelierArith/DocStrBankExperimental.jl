```
dayofweekofmonth(dt::TimeType) -> Int
```

`dt`의 주의 날에 대해, `dt`의 월에서 몇 번째인지 반환합니다. 따라서 `dt`의 주의 날이 월요일인 경우, `1 = 해당 월의 첫 번째 월요일, 2 = 두 번째 월요일, 등등.` 1:5 범위 내에서.

# 예시

```jldoctest
julia> dayofweekofmonth(Date("2000-02-01"))
1

julia> dayofweekofmonth(Date("2000-02-08"))
2

julia> dayofweekofmonth(Date("2000-02-15"))
3
```
