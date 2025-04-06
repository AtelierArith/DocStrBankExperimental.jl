```
canonicalize(::CompoundPeriod) -> CompoundPeriod
```

`CompoundPeriod`'ı aşağıdaki kuralları uygulayarak kanonik formuna indirger:

  * Yeterince büyük olan herhangi bir `Period`, daha kaba bir `Period` tarafından kısmen temsil edilebiliyorsa, birden fazla `Period`'a bölünecektir (örneğin, `Hour(30)` `Day(1) + Hour(6)` haline gelir)
  * Zıt işaretlere sahip `Period`'lar mümkün olduğunda birleştirilecektir (örneğin, `Hour(1) - Day(1)` `-Hour(23)` haline gelir)

# Örnekler

```jldoctest
julia> canonicalize(Dates.CompoundPeriod(Dates.Hour(12), Dates.Hour(13)))
1 gün, 1 saat

julia> canonicalize(Dates.CompoundPeriod(Dates.Hour(-1), Dates.Minute(1)))
-59 dakika

julia> canonicalize(Dates.CompoundPeriod(Dates.Month(1), Dates.Week(-2)))
1 ay, -2 hafta

julia> canonicalize(Dates.CompoundPeriod(Dates.Minute(50000)))
4 hafta, 6 gün, 17 saat, 20 dakika
```
