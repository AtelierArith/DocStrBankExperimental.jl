```
floor(dt::TimeType, p::Period) -> TimeType
```

주어진 `dt`보다 작거나 같은 가장 가까운 `Date` 또는 `DateTime`을 해상도 `p`로 반환합니다.

편의를 위해 `p`는 값 대신 타입일 수 있습니다: `floor(dt, Dates.Hour)`는 `floor(dt, Dates.Hour(1))`의 단축키입니다.

```jldoctest
julia> floor(Date(1985, 8, 16), Month)
1985-08-01

julia> floor(DateTime(2013, 2, 13, 0, 31, 20), Minute(15))
2013-02-13T00:30:00

julia> floor(DateTime(2016, 8, 6, 12, 0, 0), Day)
2016-08-06T00:00:00
```
