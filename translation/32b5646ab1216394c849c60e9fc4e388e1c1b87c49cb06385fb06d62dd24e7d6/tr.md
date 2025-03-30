```
daysinyear(dt::TimeType) -> Int
```

`dt` yılının artık yıl olması durumunda 366, aksi takdirde 365 döndürün.

# Örnekler

```jldoctest
julia> daysinyear(1999)
365

julia> daysinyear(2000)
366
```
