```
daysofweekinmonth(dt::TimeType) -> Int
```

`dt`의 요일에 대해, `dt`의 월에서 해당 요일의 총 수를 반환합니다. 4 또는 5를 반환합니다. 조정기 함수에서 `dayofweekofmonth(dt) == daysofweekinmonth(dt)`를 포함하여 한 달의 마지막 주의 날을 지정하는 데 유용합니다.

# 예시

```jldoctest
julia> daysofweekinmonth(Date("2005-01-01"))
5

julia> daysofweekinmonth(Date("2005-01-04"))
4
```
