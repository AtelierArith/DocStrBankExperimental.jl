```
ceil(x::Period, precision::T) where T <: Union{TimePeriod, Week, Day} -> T
```

Runde `x` auf das nächste Vielfache von `precision` auf. Wenn `x` und `precision` unterschiedliche Subtypen von `Period` sind, hat der Rückgabewert denselben Typ wie `precision`.

Zur Vereinfachung kann `precision` ein Typ anstelle eines Wertes sein: `ceil(x, Dates.Hour)` ist eine Abkürzung für `ceil(x, Dates.Hour(1))`.

```jldoctest
julia> ceil(Day(16), Week)
3 Wochen

julia> ceil(Minute(44), Minute(15))
45 Minuten

julia> ceil(Hour(36), Day)
2 Tage
```

Das Runden auf eine `precision` von `Monat`s oder `Jahr`s wird nicht unterstützt, da diese `Period`s von inkonsistenter Länge sind. ```
