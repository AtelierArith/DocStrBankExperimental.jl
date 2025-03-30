```
CompoundPeriod(periods) -> CompoundPeriod
```

`Period`의 `Vector`로부터 `CompoundPeriod`를 생성합니다. 동일한 유형의 모든 `Period`는 함께 더해집니다.

# 예시

```jldoctest
julia> Dates.CompoundPeriod(Dates.Hour(12), Dates.Hour(13))
25 hours

julia> Dates.CompoundPeriod(Dates.Hour(-1), Dates.Minute(1))
-1 hour, 1 minute

julia> Dates.CompoundPeriod(Dates.Month(1), Dates.Week(-2))
1 month, -2 weeks

julia> Dates.CompoundPeriod(Dates.Minute(50000))
50000 minutes
```
