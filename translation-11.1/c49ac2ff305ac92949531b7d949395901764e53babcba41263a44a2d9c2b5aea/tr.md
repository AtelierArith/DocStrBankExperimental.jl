```
floor(x::Period, precision::T) where T <: Union{TimePeriod, Week, Day} -> T
```

`x`'i `precision`'ın en yakın katına yuvarlayın. Eğer `x` ve `precision` farklı `Period` alt türleri ise, dönen değer `precision` ile aynı türde olacaktır.

Kolaylık olması açısından, `precision` bir değer yerine bir tür olabilir: `floor(x, Dates.Hour)` ifadesi `floor(x, Dates.Hour(1))` için bir kısayoldur.

```jldoctest
julia> floor(Day(16), Week)
2 weeks

julia> floor(Minute(44), Minute(15))
30 minutes

julia> floor(Hour(36), Day)
1 day
```

`Month` veya `Year` gibi bir `precision`'a yuvarlama desteklenmemektedir, çünkü bu `Period`'ler tutarsız uzunluktadır.
