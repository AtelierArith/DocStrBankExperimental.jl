```
week(dt::TimeType) -> Int64
```

Bir `Date` veya `DateTime`'ın [ISO hafta tarihi](https://en.wikipedia.org/wiki/ISO_week_date) olarak bir [`Int64`](@ref) döndürür. Bir yılın ilk haftası, yılın ilk Perşembe'sini içeren haftadır; bu, 4 Ocak'tan önceki tarihlerinin bir önceki yılın son haftasında olmasına neden olabilir. Örneğin, `week(Date(2005, 1, 1))` 2004'ün 53. haftasıdır.

# Örnekler

```jldoctest
julia> week(Date(1989, 6, 22))
25

julia> week(Date(2005, 1, 1))
53

julia> week(Date(2004, 12, 31))
53
```
