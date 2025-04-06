```
floor(x::Period, precision::T) where T <: Union{TimePeriod, Week, Day} -> T
```

Runde `x` auf das nächste Vielfache von `precision` ab. Wenn `x` und `precision` unterschiedliche Subtypen von `Period` sind, hat der Rückgabewert denselben Typ wie `precision`.

Zur Vereinfachung kann `precision` ein Typ anstelle eines Wertes sein: `floor(x, Dates.Hour)` ist eine Abkürzung für `floor(x, Dates.Hour(1))`.

```jldoctest
julia> floor(Day(16), Week)
2 Wochen

julia> floor(Minute(44), Minute(15))
30 Minuten

julia> floor(Hour(36), Day)
1 Tag
```

Das Runden auf eine `precision` von `Monat` oder `Jahr` wird nicht unterstützt, da diese `Period`s von inkonsistenter Länge sind. ```
