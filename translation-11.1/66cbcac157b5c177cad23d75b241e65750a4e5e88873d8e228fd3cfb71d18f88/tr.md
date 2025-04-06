```
round(x::Period, precision::T, [r::RoundingMode]) where T <: Union{TimePeriod, Week, Day} -> T
```

`x`'i `precision`'a en yakın katına yuvarlayın. Eğer `x` ve `precision` farklı `Period` alt türleri ise, dönen değer `precision` ile aynı türde olacaktır. Varsayılan olarak (`RoundNearestTiesUp`), bağlar (örneğin, 90 dakikayı en yakın saate yuvarlamak) yukarı yuvarlanacaktır.

Kolaylık olması açısından, `precision` bir değer yerine bir tür olabilir: `round(x, Dates.Hour)` ifadesi `round(x, Dates.Hour(1))` için bir kısayoldur.

```jldoctest
julia> round(Day(16), Week)
2 weeks

julia> round(Minute(44), Minute(15))
45 minutes

julia> round(Hour(36), Day)
2 days
```

`round(::Period, ::T, ::RoundingMode)` için geçerli yuvarlama modları `RoundNearestTiesUp` (varsayılan), `RoundDown` (`floor`) ve `RoundUp` (`ceil`)'dir.

`Month` veya `Year`'lar için bir `precision`'a yuvarlama desteklenmemektedir, çünkü bu `Period`'ler tutarsız uzunluktadır.
