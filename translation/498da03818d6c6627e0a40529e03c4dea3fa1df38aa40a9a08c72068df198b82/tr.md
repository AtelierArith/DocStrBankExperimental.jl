```
daysinmonth(dt::TimeType) -> Int
```

`dt`'nin ayındaki gün sayısını döndürür. Değer 28, 29, 30 veya 31 olacaktır.

# Örnekler

```jldoctest
julia> daysinmonth(Date("2000-01"))
31

julia> daysinmonth(Date("2001-02"))
28

julia> daysinmonth(Date("2000-02"))
29
```
