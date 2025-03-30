```
floor(dt::TimeType, p::Period) -> TimeType
```

`dt`'ye `p` çözünürlüğünde eşit veya daha küçük en yakın `Date` veya `DateTime` değerini döndürür.

Kolaylık olması açısından, `p` bir değer yerine bir tür de olabilir: `floor(dt, Dates.Hour)` ifadesi `floor(dt, Dates.Hour(1))` için bir kısayoldur.

```jldoctest
julia> floor(Date(1985, 8, 16), Month)
1985-08-01

julia> floor(DateTime(2013, 2, 13, 0, 31, 20), Minute(15))
2013-02-13T00:30:00

julia> floor(DateTime(2016, 8, 6, 12, 0, 0), Day)
2016-08-06T00:00:00
```
