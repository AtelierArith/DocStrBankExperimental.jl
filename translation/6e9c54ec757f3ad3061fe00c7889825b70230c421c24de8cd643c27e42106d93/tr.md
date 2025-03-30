```
firstdayofweek(dt::TimeType) -> TimeType
```

`dt`'yi haftasının Pazartesi gününe ayarlar.

# Örnekler

```jldoctest
julia> firstdayofweek(DateTime("1996-01-05T12:30:00"))
1996-01-01T00:00:00
```
