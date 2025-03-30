```
dayofweek(dt::TimeType) -> Int64
```

Haftanın gününü [`Int64`](@ref) olarak döndürür; `1 = Pazartesi, 2 = Salı, vb.`.

# Örnekler

```jldoctest
julia> dayofweek(Date("2000-01-01"))
6
```
