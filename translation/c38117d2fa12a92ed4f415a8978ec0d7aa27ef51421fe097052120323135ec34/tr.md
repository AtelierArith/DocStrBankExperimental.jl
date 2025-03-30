```
CompoundPeriod(periods) -> CompoundPeriod
```

Bir `Period`'lerin `Vector`'ından bir `CompoundPeriod` oluşturur. Aynı türdeki tüm `Period`'ler bir araya getirilecektir.

# Örnekler

```jldoctest
julia> Dates.CompoundPeriod(Dates.Hour(12), Dates.Hour(13))
25 saat

julia> Dates.CompoundPeriod(Dates.Hour(-1), Dates.Minute(1))
-1 saat, 1 dakika

julia> Dates.CompoundPeriod(Dates.Month(1), Dates.Week(-2))
1 ay, -2 hafta

julia> Dates.CompoundPeriod(Dates.Minute(50000))
50000 dakika
```
