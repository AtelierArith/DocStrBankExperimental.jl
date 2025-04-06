```
dayofweekofmonth(dt::TimeType) -> Int
```

`dt`'nin haftanın günü için, `dt`'nin ayındaki hangi numara olduğunu döndür. Yani, eğer `dt`'nin haftanın günü Pazartesi ise, o zaman `1 = Ayın İlk Pazartesi'si, 2 = Ayın İkinci Pazartesi'si, vb.` 1:5 aralığında.

# Örnekler

```jldoctest
julia> dayofweekofmonth(Date("2000-02-01"))
1

julia> dayofweekofmonth(Date("2000-02-08"))
2

julia> dayofweekofmonth(Date("2000-02-15"))
3
```
