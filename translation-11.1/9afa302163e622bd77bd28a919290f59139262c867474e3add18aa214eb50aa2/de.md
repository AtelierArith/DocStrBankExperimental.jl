```
round(dt::TimeType, p::Period, [r::RoundingMode]) -> TimeType
```

Gibt das `Date` oder `DateTime` zurück, das `dt` am nächsten liegt, mit der Auflösung `p`. Standardmäßig (`RoundNearestTiesUp`) werden bei Gleichständen (z. B. das Runden von 9:30 auf die nächste Stunde) die Werte nach oben gerundet.

Zur Vereinfachung kann `p` auch ein Typ anstelle eines Wertes sein: `round(dt, Dates.Hour)` ist eine Abkürzung für `round(dt, Dates.Hour(1))`.

```jldoctest
julia> round(Date(1985, 8, 16), Month)
1985-08-01

julia> round(DateTime(2013, 2, 13, 0, 31, 20), Minute(15))
2013-02-13T00:30:00

julia> round(DateTime(2016, 8, 6, 12, 0, 0), Day)
2016-08-07T00:00:00
```

Gültige Rundungsmodi für `round(::TimeType, ::Period, ::RoundingMode)` sind `RoundNearestTiesUp` (Standard), `RoundDown` (`floor`) und `RoundUp` (`ceil`).
