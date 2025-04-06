```
round(x::Period, precision::T, [r::RoundingMode]) where T <: Union{TimePeriod, Week, Day} -> T
```

Runde `x` auf das nächste Vielfache von `precision`. Wenn `x` und `precision` unterschiedliche Subtypen von `Period` sind, hat der Rückgabewert denselben Typ wie `precision`. Standardmäßig (`RoundNearestTiesUp`) werden bei Gleichständen (z. B. das Runden von 90 Minuten auf die nächste Stunde) die Werte aufgerundet.

Zur Vereinfachung kann `precision` auch ein Typ anstelle eines Wertes sein: `round(x, Dates.Hour)` ist eine Abkürzung für `round(x, Dates.Hour(1))`.

```jldoctest
julia> round(Day(16), Week)
2 weeks

julia> round(Minute(44), Minute(15))
45 minutes

julia> round(Hour(36), Day)
2 days
```

Gültige Rundungsmodi für `round(::Period, ::T, ::RoundingMode)` sind `RoundNearestTiesUp` (Standard), `RoundDown` (`floor`) und `RoundUp` (`ceil`).

Das Runden auf eine `precision` von `Month`s oder `Year`s wird nicht unterstützt, da diese `Period`s inkonsistente Längen haben.
