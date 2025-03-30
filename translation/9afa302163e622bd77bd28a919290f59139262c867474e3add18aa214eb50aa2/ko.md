```
round(dt::TimeType, p::Period, [r::RoundingMode]) -> TimeType
```

`dt`에 대해 해상도 `p`로 가장 가까운 `Date` 또는 `DateTime`을 반환합니다. 기본값(`RoundNearestTiesUp`)에서는 동점(예: 9:30을 가장 가까운 시간으로 반올림할 때)이 위로 반올림됩니다.

편의를 위해 `p`는 값 대신 타입일 수 있습니다: `round(dt, Dates.Hour)`는 `round(dt, Dates.Hour(1))`의 단축키입니다.

```jldoctest
julia> round(Date(1985, 8, 16), Month)
1985-08-01

julia> round(DateTime(2013, 2, 13, 0, 31, 20), Minute(15))
2013-02-13T00:30:00

julia> round(DateTime(2016, 8, 6, 12, 0, 0), Day)
2016-08-07T00:00:00
```

`round(::TimeType, ::Period, ::RoundingMode)`에 대한 유효한 반올림 모드는 `RoundNearestTiesUp`(기본값), `RoundDown`(`floor`), 및 `RoundUp`(`ceil`)입니다.
