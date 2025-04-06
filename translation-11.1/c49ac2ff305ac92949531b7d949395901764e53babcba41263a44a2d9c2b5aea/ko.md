```
floor(x::Period, precision::T) where T <: Union{TimePeriod, Week, Day} -> T
```

`x`를 `precision`의 가장 가까운 배수로 내림합니다. `x`와 `precision`이 서로 다른 `Period`의 하위 유형인 경우, 반환 값은 `precision`과 동일한 유형이 됩니다.

편의를 위해 `precision`은 값 대신 유형일 수 있습니다: `floor(x, Dates.Hour)`는 `floor(x, Dates.Hour(1))`의 단축키입니다.

```jldoctest
julia> floor(Day(16), Week)
2 weeks

julia> floor(Minute(44), Minute(15))
30 minutes

julia> floor(Hour(36), Day)
1 day
```

`Month` 또는 `Year`의 `precision`으로 반올림하는 것은 지원되지 않습니다. 이러한 `Period`는 길이가 일관되지 않기 때문입니다.
