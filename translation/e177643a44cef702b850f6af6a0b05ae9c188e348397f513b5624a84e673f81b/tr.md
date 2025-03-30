```
ceil(x::Period, precision::T) where T <: Union{TimePeriod, Week, Day} -> T
```

`x`'i `precision`'ın en yakın katına yuvarlayın. Eğer `x` ve `precision` farklı `Period` alt türleri ise, dönen değer `precision` ile aynı türde olacaktır.

Kolaylık olması açısından, `precision` bir değer yerine bir tür olabilir: `ceil(x, Dates.Hour)` ifadesi `ceil(x, Dates.Hour(1))` için bir kısayoldur.

```jldoctest
julia> ceil(Day(16), Week)
3 weeks

julia> ceil(Minute(44), Minute(15))
45 minutes

julia> ceil(Hour(36), Day)
2 days
```

`Month` veya `Year`'ler için bir `precision` ile yuvarlama desteklenmemektedir, çünkü bu `Period`'ler tutarsız uzunluktadır.
