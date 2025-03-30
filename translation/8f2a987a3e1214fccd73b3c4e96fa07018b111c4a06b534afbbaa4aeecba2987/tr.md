```
lastdayofweek(dt::TimeType) -> TimeType
```

`dt`'yi haftasının Pazar gününe ayarlar.

# Örnekler

```jldoctest
julia> lastdayofweek(DateTime("1996-01-05T12:30:00"))
1996-01-07T00:00:00
```
