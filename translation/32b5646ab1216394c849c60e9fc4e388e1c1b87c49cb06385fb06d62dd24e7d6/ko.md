```
daysinyear(dt::TimeType) -> Int
```

`dt`의 연도가 윤년이면 366을 반환하고, 그렇지 않으면 365를 반환합니다.

# 예제

```jldoctest
julia> daysinyear(1999)
365

julia> daysinyear(2000)
366
```
