```
lastdayofquarter(dt::TimeType) -> TimeType
```

`dt`'yi çeyreğinin son gününe ayarlar.

# Örnekler

```jldoctest
julia> lastdayofquarter(DateTime("1996-05-20"))
1996-06-30T00:00:00

julia> lastdayofquarter(DateTime("1996-08-20"))
1996-09-30T00:00:00
```
