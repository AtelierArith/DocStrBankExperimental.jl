```
canonicalize(::CompoundPeriod) -> CompoundPeriod
```

`CompoundPeriod`를 다음 규칙을 적용하여 정준형으로 축소합니다:

  * 더 거친 `Period`로 부분적으로 표현될 수 있을 만큼 큰 `Period`는 여러 개의 `Period`로 나뉩니다 (예: `Hour(30)`는 `Day(1) + Hour(6)`로 변환됩니다)
  * 반대 부호의 `Period`는 가능할 때 결합됩니다 (예: `Hour(1) - Day(1)`은 `-Hour(23)`로 변환됩니다)

# 예제

```jldoctest
julia> canonicalize(Dates.CompoundPeriod(Dates.Hour(12), Dates.Hour(13)))
1 day, 1 hour

julia> canonicalize(Dates.CompoundPeriod(Dates.Hour(-1), Dates.Minute(1)))
-59 minutes

julia> canonicalize(Dates.CompoundPeriod(Dates.Month(1), Dates.Week(-2)))
1 month, -2 weeks

julia> canonicalize(Dates.CompoundPeriod(Dates.Minute(50000)))
4 weeks, 6 days, 17 hours, 20 minutes
```
