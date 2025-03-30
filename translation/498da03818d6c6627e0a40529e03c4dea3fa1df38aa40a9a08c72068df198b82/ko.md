```
daysinmonth(dt::TimeType) -> Int
```

`dt`의 월에 있는 일 수를 반환합니다. 값은 28, 29, 30 또는 31이 됩니다.

# 예시

```jldoctest
julia> daysinmonth(Date("2000-01"))
31

julia> daysinmonth(Date("2001-02"))
28

julia> daysinmonth(Date("2000-02"))
29
```
