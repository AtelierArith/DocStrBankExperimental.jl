```
trunc(dt::TimeType, ::Type{Period}) -> TimeType
```

`dt` değerini sağlanan `Period` türüne göre keser.

# Örnekler

```jldoctest
julia> trunc(DateTime("1996-01-01T12:30:00"), Day)
1996-01-01T00:00:00
```
