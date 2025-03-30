```
round(dt::TimeType, p::Period, [r::RoundingMode]) -> TimeType
```

`dt`'ye en yakın `Date` veya `DateTime`'ı `p` çözünürlüğünde döndürür. Varsayılan olarak (`RoundNearestTiesUp`), bağlar (örneğin, 9:30'u en yakın saate yuvarlama) yukarı yuvarlanacaktır.

Kolaylık olması açısından, `p` bir değer yerine bir tür olabilir: `round(dt, Dates.Hour)` ifadesi `round(dt, Dates.Hour(1))` için bir kısayoldur.

```jldoctest
julia> round(Date(1985, 8, 16), Month)
1985-08-01

julia> round(DateTime(2013, 2, 13, 0, 31, 20), Minute(15))
2013-02-13T00:30:00

julia> round(DateTime(2016, 8, 6, 12, 0, 0), Day)
2016-08-07T00:00:00
```

`round(::TimeType, ::Period, ::RoundingMode)` için geçerli yuvarlama modları `RoundNearestTiesUp` (varsayılan), `RoundDown` (`floor`) ve `RoundUp` (`ceil`)'dir.
