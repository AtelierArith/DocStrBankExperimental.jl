```
round(x::Period, precision::T, [r::RoundingMode]) where T <: Union{TimePeriod, Week, Day} -> T
```

`x`를 `precision`의 가장 가까운 배수로 반올림합니다. `x`와 `precision`이 서로 다른 `Period`의 하위 유형인 경우, 반환 값은 `precision`과 동일한 유형이 됩니다. 기본값(`RoundNearestTiesUp`)에서는 동점(예: 90분을 가장 가까운 시간으로 반올림할 때)이 위로 반올림됩니다.

편의를 위해 `precision`은 값 대신 유형일 수 있습니다: `round(x, Dates.Hour)`는 `round(x, Dates.Hour(1))`의 단축키입니다.

```jldoctest
julia> round(Day(16), Week)
2 weeks

julia> round(Minute(44), Minute(15))
45 minutes

julia> round(Hour(36), Day)
2 days
```

`round(::Period, ::T, ::RoundingMode)`에 대한 유효한 반올림 모드는 `RoundNearestTiesUp`(기본값), `RoundDown`(`floor`), 및 `RoundUp`(`ceil`)입니다.

`Month` 또는 `Year`의 `precision`으로 반올림하는 것은 지원되지 않으며, 이러한 `Period`는 길이가 일관되지 않기 때문입니다.
