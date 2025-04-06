```
daysofweekinmonth(dt::TimeType) -> Int
```

`dt`'nin haftanın günü için, `dt`'nin ayındaki o haftanın günlerinin toplam sayısını döndürür. 4 veya 5 döner. Bir ay içindeki haftanın son gününü belirtmek için `dayofweekofmonth(dt) == daysofweekinmonth(dt)` ifadesini ayarlayıcı fonksiyona dahil ederek zamansal ifadelerde kullanışlıdır.

# Örnekler

```jldoctest
julia> daysofweekinmonth(Date("2005-01-01"))
5

julia> daysofweekinmonth(Date("2005-01-04"))
4
```
